**Example**

The following example adds the two vectors `[1, 2, 5]` and `[3, 4, -1]` as `1+3`, `2+4`, and `5+(-1)`, which yields to `[4, 6, 3]`.

**Returns**
``` sql
select vector_add([1, 2, 5], [3, 4, -2]) as res
```

| res (ARRAY(BIGINT)) |
| :--- |
| {4 | 6 | 3} |