# 2. Values and text

## Create a value

`Define` creates a named value. `Set` changes it.

```text
Define Count = 3
Set Count = Count + 1
Write = Count is now {Count}
```

```text
Count is now 4
```

A name starts with a letter and may contain letters, digits and `_`.
Capital letters do not matter: `Count`, `count` and `COUNT` are one name.

## Kinds of values

| Kind | Examples |
|---|---|
| Number | `5`, `3.14`, `-2` |
| Text | `Hello`, `"Hello, world"` |
| Switch | `ON`, `OFF` (also `TRUE`, `FALSE`) |
| List | `List 1, 2, 3` (see [lists](lists.md)) |
| Nothing | `Nothing` |

## Calculations

```text
Define Width = 4
Define Height = 5
Write = Area: {Width * Height}
```

| Sign | Meaning |
|---|---|
| `+` `-` | add, subtract |
| `*` `/` | multiply, divide |
| `%` | remainder after dividing |
| `^` | power: `2 ^ 3` is 8 |
| `( )` | calculate this part first |

`+` also joins text: `{"Jadiv" + "Code"}` gives `JadivCode`.

## Text or calculation?

After `=`, JadivCode looks at what you wrote:

- If it is a complete calculation made of numbers and names that exist, it
  is **calculated**.
- Otherwise it is **text**.

```text
Define Price = 10
Write = Price * 2          // 20      (a calculation)
Write = Price is too high  // text    ("is too high" is not a calculation)
Write = "Price * 2"        // text    (quotes always mean text)
Write = It costs {Price * 2} EUR   // text with a value inside
```

!!! tip "Two simple rules"
    Put **quotes** around text when you want to be sure it stays text.
    Put **curly braces** around a value inside text.

To write a real curly brace in text, double it: `{{` and `}}`.

## Built-in helpers

Helpers are used inside `{ }` or after `=`.

| Helper | Result |
|---|---|
| `Length(X)` | number of characters in text, or items in a list |
| `Upper(X)`, `Lower(X)` | text in capital / small letters |
| `Trim(X)` | text without spaces at both ends |
| `Number(X)` | text turned into a number |
| `Text(X)` | a value turned into text |
| `Round(X)`, `Round(X, 2)` | rounded number (2 decimal places) |
| `Contains(X, Y)` | `ON` when X contains Y |
| `Replace(X, Old, New)` | text with every Old replaced by New |
| `Split(X, ",")` | text cut into a list |
| `Join(List, ", ")` | a list joined into text |
| `Type(X)` | `Number`, `Text`, `Switch`, `List`, `Map` or `Nothing` |

```text
Ask Name = Your name?
Write = {Upper(Name)} has {Length(Name)} letters
```

Next: [decisions](decisions.md).
