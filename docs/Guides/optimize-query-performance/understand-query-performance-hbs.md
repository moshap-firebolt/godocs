---
layout: default
title: Understanding History-based Optimization
description: How to understand history-based query optimization
parent: Optimize query performance
nav_order: 1
has_toc: false
has_children: false
---

# Understanding History-based Optimization

## Overview

Firebolt's query plans evolve with your workload over time.
Firebolt implements a feedback loop that enables our query optimizer to learn and improve based on past queries.
It is designed to progressively come up with better query plans and thereby steadily improve the performance of your queries towards the optimal.

## Scope of history-based optimizations
Firebolt's history-based optimization techniques include the following:
- **Join ordering** ---
  The sequence in which tables are joined during query processing, especially in complex queries with multiple tables, can significantly affect query performance.
  Firebolt uses query statistics and historical patterns to determine the most efficient join order that optimizes both run times and resource utilization.
- **Aggregating index selection** ---
  Firebolt analyzes historical query patterns to identify the most frequently used aggregating indexes, which store pre-computed aggregates such as `SUM`, `AVG`, and `COUNT`.
  It then suggests indexes to reduce computational load during query processing.
- **Semi-join and anti-join planning** ---
  Firebolt's query planner selects the most efficient way to run semi-joins, which return matching rows, and anti-joins, which return rows with no match in another table.
- **Broadcast and shuffle strategies for multi-node engines** ---
  Firebolt uses a broadcast strategy for small datasets that can be efficiently distributed across all nodes to minimize data movement, and a shuffle strategy when both datasets are large.
  Implementing these strategies can greatly improve query performance for distributed joins by optimizing how data is distributed and processed across multiple nodes.

## How it works

When you run a query, Firebolt's query optimizer constructs a query plan to run the process efficiently.
After running the query, the collected telemetry is fed back into Firebolt's history snapshot.
When you run the next query, the query optimizer accesses the telemetry that was collected in that history snapshot and extracts from it statistical information.
Consequently, previously run queries aid the query optimizer in finding better query plans for subsequent queries and thereby improve performance.

<img src="../../assets/images/history-based-optimization.png" alt="Telemetry data flows back from the runtime into the query optimizer where the next run is planned." width="700"/>

### Recording query history

Firebolt’s query optimizer continually improves runtime performance by recording telemetry data from your past queries and extracting statistical information from it.
This process runs automatically in the background without user intervention.

Firebolt stores in its history snapshot only the query plan of a query together with its telemetry data.
The telemetry contains information for each operator of the query plan, e.g. how many rows and bytes of data an operator processed, how much time passed, or how much memory was consumed.
The query plan contains the original query string.
This means, if the original query contains PII, so does the query plan, and hence PII is stored in the history snapshot.
The query result of the query is not considered in any way by history-based optimization.
If the query result contains PII, you can rest assured that it is not stored in the history snapshot.
While PII from the original query string is stored in the history snapshot, the snapshot is guarded against unauthorized access;
only engines running on the same database -- and hence the same account -- and authorized Firebolt personnel can access the snapshot.

### Planning queries based on history

When you submit a query, Firebolt analyzes its recorded history to predict how different query plans will perform, and chooses one that should deliver the best performance.
This query history is released to the query optimizer every `10` minutes in the form of a history-based statistics (HBS) snapshot.

Each engine has a dedicated HBS component that is always active, continuously generating snapshots for the engine to reference during query planning.
These snapshots are saved and shared among all engines running on the same database within the same account.
Consequently, an engine can benefit from the query history from another engine, improving performance across all engines without needing to restart the analysis process.
After engine restart, the engine retrieves the latest HBS snapshot.

## Observability

The Firebolt query optimizer uses HBS in the scenarios listed in the scope section above.
To see whether history-based statistics were used when planning your query, use `EXPLAIN` with the `statistics` option, as follows:

```sql
EXPLAIN (statistics)
select ...  -- your query goes here
```

The `EXPLAIN` option `statistics` annotates all nodes of the query plan with the sources of statistics used in its cost estimation.
An example of the `EXPLAIN (statistics)` output below shows `source: history`, and we know that the estimates were made based on history.

```plain
[Logical Profile]: [source: history]
```

For more information about output from `EXPLAIN (statistics)`, including various possible values that the source field can take, see [Explain: Example with statistics](../../sql_reference/commands/queries/explain.html#example-with-statistics).

The `EXPLAIN(statistics)` output will not show `source:history` during the first run of an alternate query plan if the optimizer finds that the initial query plan was not optimal. This absence occurs because the alternative plan has not yet gathered telemetry data during its initial run.
In the next execution of the same query, the optimizer understands that it should choose an alternative plan to avoid the slow execution.
This means, that history-based statistics are in effect, but we may not see `history` shown in sources of the `EXPLAIN (statistics)` output for the new run.
It could be that for the alternative plan we have not collected its execution telemetry yet.