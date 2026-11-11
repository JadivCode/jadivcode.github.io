# 5. Lists

A list holds several values under one name.

```text
Define Colors = List red, green, blue
Write = {Colors}
```

```text
red, green, blue
```

## Reading items

Items are numbered from 1. Use `#` and the position:

```text
Write = First: {Colors #1}
Write = There are {Length(Colors)} colors
```

## Changing a list

```text
Add yellow to Colors
Remove green from Colors
```

## Going through a list

```text
For each Color in Colors
    Write = I like {Color}
End
```

## Useful helpers

| Helper | Result |
|---|---|
| `Length(L)` | number of items |
| `Contains(L, X)` | `ON` when X is in the list |
| `Join(L, " - ")` | all items as one text |
| `Split("a,b,c", ",")` | text cut into a list |

An empty list is written `Define Names = List`.

Next: [functions](functions.md).
