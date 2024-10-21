---
layout: default
title: What is Firebolt?
description: Product overview
nav_order: 2
has_toc: true
has_children: true
---

# What is Firebolt?

Firebolt is a next-generation cloud data warehouse designed for organizations that require lightning-fast analytics at scale. Whether you're dealing with complex data applications, high-concurrency workloads, or low-latency queries, Firebolt empowers you to unlock the full potential of your data without compromising on performance or cost.

# Why Firebolt?

Firebolt was designed specifically to meet the demands of modern data workloads, focusing on delivering exceptional efficiency at a low cost while maintaining industry-leading performance for data-intensive applications.

Firebolt helps to alleviate the following challenges:

* High latency and costly performance during data processing and retrieval.
* Poor query performance under heavy loads.
* Difficulty in scaling to manage large datasets efficiently.
* Complexity in managing and optimizing data workflows, with limited compatibility with existing tools and unfamiliar languages.

The following sections highlight Firebolt's key benefits, as well as its compatibility with various frameworks and workloads for seamless data integration and processing:

* [Key benefits](#key-benefits)
* [Frameworks and workloads](#frameworks-and-workloads)

# Key benefits

Firebolt provides scalability, so that you can respond rapidly to changes in your data and workloads with the following key benefits:

* [High Efficiency](#high-efficiency) — Achieve exceptional price-to-performance ratios, providing high-speed analytics without the high costs.
* [Concurrency at Scale](#concurrency-at-scale) — Run thousands of queries concurrently while maintaining sub-second performance.
* [Elasticity](#elasticity) — Seamlessly scale to handle hundreds of terabytes of data without sacrificing speed or efficiency.
* [SQL Simplicity](#sql-simplicity) — Benefit from SQL compatibility with a subset of PostgreSQL, making it easy for teams to adopt with minimal training.

### <img src="../../assets/images/icon-efficiency.png" alt="Icon for efficiency." width="40"/> High efficiency

Firebolt delivers high efficiency and low latency for immediate insights while offering one of the best price-to-performance ratios in the industry. Its architecture is optimized for fast query execution through features like vectorized processing and sparse indexing, which minimize data scans and maximize CPU efficiency. This results in quicker responses to data-intensive queries, even at petabyte scale, without overloading compute resources. Whether analyzing structured or semi-structured data, Firebolt enables millisecond-response times with the added assurance of ACID compliance, guaranteeing the consistency and reliability of your data.

### <img src="../../assets/images/icon-concurrency.png" alt="Icon for concurrency at scale." width="40"/> Concurrency at scale

Firebolt supports thousands of concurrent queries, ensuring that your applications can handle heavy query loads while maintaining consistent, reliable performance. Fine-grained scaling options allow Firebolt to process high throughput efficiently, even under the most demanding workloads.

### <img src="../../assets/images/icon-elasticity.png" alt="Icon for elasticity or vertical, horizontal or concurrent scaling." width="40"/> Elasticity

Firebolt's fully decoupled architecture and multi-dimensional elasticity scalability allow compute, storage, and management resources to scale independently, optimizing both performance and cost efficiency. You can access any database from any engine, giving you so you have fine-grained control over resources as your workload changes, including scaling out for massive datasets. Firebolt’s architecture supports:

* **Vertical scaling** - Scale up to increase the capacity of your engine to handle complex queries or data-intensive workloads.
* **Horizontal scaling** - Scale-out to increase the number of compute nodes to handle higher data processing demands.
* **Concurrent scaling** - Run multiple clusters within a single engine, which can scale up to ten clusters simultaneously. User applications automatically benefit from concurrent scaling without any endpoint changes, as Firebolt manages their scaling transparently.

The following diagram includes code examples of how to scale vertically, horizontally or concurrently using SQL in the **Firebolt Workspace**:

<img src="../../assets/images/product-scaling-engines.png" alt="You can scale vertically, horizontally, or concurrently in the Firebolt Workspace." width="700"/>


This multi-dimensional approach to elasticity ensures Firebolt can adjust dynamically to any workload, keeping your system optimized and cost-effective.

### <img src="../../assets/images/icon-simplicity.png" alt="Icon for SQL simplicity." width="40"/> SQL simplicity

Firebolt supports a PostgreSQL-compliant SQL dialect, allowing your teams to harness the power of Firebolt without the need to learn a new query language. This simplifies data provisioning, processing, and management tasks, ensuring compatibility with existing workflows. Firebolt supports both structured and [semi-structured data](../Guides/working-with-semi-structured-data/), so that you can analyze diverse datasets within a single platform.

# Frameworks and workloads

Firebolt’s platform is optimized for integration within modern data workflows. It supports ingesting data efficiently through ELT tools, making it easy to move data from data lakes, relational databases, and other source systems into Firebolt. With support for Amazon S3 cloud storage and popular file formats like Avro, Parquet and ORC, Firebolt allows you to centralize and query your data with ultra-fast analytics, seamlessly fitting into your existing data architecture.

You can leverage industry-standard tools like Apache Airflow, dbt, and Superset for orchestration and visualization. Firebolt’s SDKs support a wide range of language clients like Python, Node.js, Java, and .NET. This flexibility empowers your team to build and query data using their preferred environments, ensuring smooth data workflows from ingestion to advanced analytics.

<img src="../../assets/images/firebolt-framework.png" alt="Firebolt supports popular SDKs and connectors to integrate with many workflows." width="700"/>

### <img src="../../assets/images/icon-isolation.png" alt="Icon for workload isolation." width="40"/> Workload isolation for smooth operations

Firebolt takes into account configuration, resource utilization, and history-based statistics to optimize workloads for both latency and throughput. Any Firebolt engine can execute both read and write operations on data stored in any database while maintaining strong consistency across all engines.  Each workload is managed independently with dedicated compute resources, allowing you to run complex ELT processes, fast queries, BI reports, among others, without interference. This isolation ensures that resource-heavy tasks do not impact your most critical applications and dashboards, enabling smooth operations across diverse use cases.

# Next steps

Read about Firebolt's [platform capabilities](../product/product-platform.md).

Learn how to load and query your data with our [Get Started](../Guides/getting-started/index.md) and [Load data](../Guides/loading-data/loading-data.md) guides or use one of Firebolt’s [test data sets](https://www.firebolt.io/free-sample-datasets). 

<a
    data-cta-button="true"
    data-cta-position="hero"
    data-cta-action="signup"
    href="https://go.firebolt.io/signup"
    class="cta-arrow pricing w-inline-block">
Sign-up</a> to access your $200 Firebolt credit. No credit card needed



# More Firebolt resources

* See news, blog posts, whitepapers, events and videos at [Firebolt's Knowledge center](https://www.firebolt.io/knowledge-center). 
* Explore our [competitive pricing options](https://www.firebolt.io/pricing).

Need help? Firebolt’s support team at [support@firebolt.io](mailto:support@firebolt.io) is here to assist you with:

* Getting help with onboarding.
* Troubleshooting query performance.
* Optimizing database configurations.
* Addressing data loading issues.
* Getting best practices for data modeling.

{: .no_toc}
