---
layout: default
title: VECTOR_SUBTRACT
description: Reference material for VECTOR_SUBTRACT function
parent: Vector functions
---

## VECTOR_SUBTRACT

Returns an array which is the result of the subtraction of the two input arrays.

## Syntax
{: .no_toc}

```sql
VECTOR_SUBTRACT(<array>, <array>)
```
## Parameters
{: .no_toc}

| Parameter | Description                                        | Supported input types                                           |
|:----------|:---------------------------------------------------|:----------------------------------------------------------------|
| `<array>` | The first array used in the subtract calculation.  | Any array of [numeric data types](../../data-types.md#numeric). |
| `<array>` | The second array used in the subtract calculation. | Any array of [numeric data types](../../data-types.md#numeric). |

## Notes
Both input `array` arguments must have the same number of elements.

## Return Type
The return type is `ARRAY(BIGINT)` if the element type of `<array>` is `INT` and `ARRAY(DOUBLE PRECISION)` if the element type is `REAL`. Otherwise, it matches the element type.

## Examples
{: .no_toc}

{% include sql_examples/vector_subtract.md %}
