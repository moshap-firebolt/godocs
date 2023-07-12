---
layout: default
title: LOWER
description: Reference material for LOWER function
grand_parent: SQL functions
parent: String functions
---

# LOWER

Converts the string to a lowercase format.

## Syntax
{: .no_toc}

```sql
LOWER(<string>)
```

| Parameter  | Description                 |
| :---------- | :--------------------------- |
| `<string>` | The string to be converted. |

## Return Type
The return type for this function includes `CHAR`. 

## Example
{: .no_toc}
The following example converts a video game player's username from lower case syntax to all uppercase syntax:

```
SELECT
	LOWER('ESIMPSON');
```

**Returns**: `esimpson`