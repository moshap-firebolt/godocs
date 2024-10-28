**Example**

The following example subtracts the vector `[3, 4, -4]` from `[1, 5, 6]` as `1-3`, `5-4`, and `6-(-2)`, which yields to `[-2, 1, 8]`.

**Returns**
``` sql
select vector_subtract([1, 5, 6], [3, 4, -2]) as res
```

| res (ARRAY(BIGINT)) |
| :--- |
| {-2 | 1 | 8} |