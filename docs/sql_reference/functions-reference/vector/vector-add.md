---
layout: default
title: VECTOR_ADD
description: Reference material for VECTOR_ADD function
parent: Vector functions
---

## VECTOR_ADD

Returns an array which is the result of the addition of the two input arrays.

## Syntax
{: .no_toc}

```sql
VECTOR_ADD(<array>, <array>)
```
## Parameters
{: .no_toc}

| Parameter | Description                                        | Supported input types                                           |
|:----------|:---------------------------------------------------|:----------------------------------------------------------------|
| `<array>` | The first array used in the addition calculation.  | Any array of [numeric data types](../../data-types.md#numeric). |
| `<array>` | The second array used in the addition calculation. | Any array of [numeric data types](../../data-types.md#numeric). |

## Notes
Both input `array` arguments must have the same number of elements.

## Return Type
The return type is `ARRAY(BIGINT)` if the element type of `<array>` is `INT` and `ARRAY(DOUBLE PRECISION)` if the element type is `REAL`. Otherwise, it matches the element type.

## Examples
{: .no_toc}

{% include sql_examples/vector_add.md %}
