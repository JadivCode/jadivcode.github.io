# Language reference

Every statement of JadivCode, in alphabetical order. For a gentle
introduction read [Learn](learn/first-program.md) first.

## How a program is read

- One statement per line. Empty lines are ignored.
- Text after `//` is a comment. A line that starts with `#` and a space is
  a comment too.
- Names and keywords are not case sensitive.
- A name starts with a letter and may contain letters, digits and `_`.
- Blocks (`If`, `Repeat`, `While`, `Forever`, `For`, `Function`, `On`) end
  with `End`. Indenting is optional.

## Values after `=`

What follows `=` is **calculated** when it is a complete calculation made
of numbers, quoted text and names that exist. Otherwise it is **text**, in
which every `{ }` is replaced by its value.

| Written | Result |
|---|---|
| `Set A = 2 + 3` | the number 5 |
| `Set A = Price * 2` | a number, when `Price` exists |
| `Set A = Hello there` | the text `Hello there` |
| `Set A = "2 + 3"` | the text `2 + 3` |
| `Set A = Total: {2 + 3}` | the text `Total: 5` |
| `Set A = {Items}` | the list itself (a lone `{ }` keeps its kind) |
| `Set A = List 1, 2, 3` | a list |

Write `{{` and `}}` for real curly braces.

## Operators

| Operator | Meaning |
|---|---|
| `+` `-` `*` `/` | add (or join text), subtract, multiply, divide |
| `%` | remainder |
| `^` | power |
| `=` `is` | equal (text ignores capitals) |
| `==` | exactly equal |
| `!=` `<>` `is not` | not equal |
| `<` `>` `<=` `>=` | compare |
| `and` `or` `not` | combine conditions |
| `X #2`, `X #"name"` | item 2 of a list, or a named field of a map |
| `( )` | calculate this part first |

Calculation order: `^`, then `* / %`, then `+ -`, then comparisons, then
`not`, `and`, `or`.

In a condition, `{X}` means the same as `(X)`.

## Statements

### Add

```text
Add <value> to <List>
```

Adds an item to the end of a list.

### Ask

```text
Ask <Name> = <question>
```

Shows the question, waits for a line of input and stores it. An answer
that is a number is stored as a number.

### Break

Leaves the nearest loop.

### Call

```text
Call <Function> <value>, <value>
```

Runs a function. Functions that return a value are used as
`{Function(value, value)}` instead.

### Continue

Jumps to the next round of the nearest loop.

### Define

```text
Define <Name> = <value>
Define <Name> = <Library> <command>
Define <Name> = <Library> <command with {}>
```

Creates a named value, a named thing of a library, or a
[shortcut](learn/libraries.md#shortcuts).

### Else, Else If

Part of [`If`](#if).

### End

Closes a block.

### Exit

The same as `Stop` without a name.

### For

```text
For <Name> = <first> to <last>
For <Name> = <first> to <last> step <step>
For each <Name> in <List>
```

Counts from first to last (downwards when last is smaller), or goes
through a list, the characters of a text or the names in a map.

### Forever

```text
Forever
    ...
End
```

Repeats until `Break` or `Stop`. Put a `Wait` inside.

### Function

```text
Function <Name> <parameter>, <parameter>
    ...
    Return <value>
End
```

Defines a function. It must appear above its first use. Names created
inside exist only inside; names of the main program can be read and
changed.

### If

```text
If <condition> then <statement>
If <condition> then <statement> else <statement>

If <condition>
    ...
Else If <condition>
    ...
Else
    ...
End
```

In the one-line form each statement may be put in quotes.

### Import

```text
Import <Library>
Import <Library>, <Library>
```

Makes a library usable. See [Libraries](libraries/gpio.md).

### On

```text
On <event> "<statement>"
On <event> "<statement>" Else loop

On <event>
    ...
End
```

Runs statements each time the event happens. An event is a named thing
(`On Go`), a thing with a word (`On Button Pressed`), a shortcut with
values (`On Hook "/lamp"`) or a library command. Inside, `Event` holds what
happened.

### Remove

```text
Remove <value> from <List>
```

Removes the first matching item.

### Repeat

```text
Repeat <number> times
    ...
End
```

### Return

```text
Return <value>
```

Ends a function and hands a value back. The value is optional.

### Set

```text
Set <Name> = <value>
Set <Name> <Property> = <value>
```

Changes a value, or creates it when it does not exist yet. When the name
holds a thing, `Set` changes the thing: a pin is switched, an item gets new
text.

### Start

```text
Start <Name>
```

Starts a thing: shows a window, starts a web page or a webhook server.

### Stop

```text
Stop
Stop <Name>
```

Without a name, ends the program. With a name, stops or removes that thing.

### Strict

```text
Strict ON
Strict OFF
```

With `Strict ON` the first problem stops the program.

### Wait

```text
Wait <number><unit>
```

Units: `ms`, `s`, `m`, `h`. Without a unit the number means seconds.
Windows, web pages and events keep working while the program waits.

### While

```text
While <condition>
    ...
End
```

### Write

```text
Write = <value>
```

Shows a value on screen. `ON`/`OFF` are shown for switches, and a list is
shown with commas.

## Built-in names

| Name | Value |
|---|---|
| `Success` | `Full`, `Partial` or `None` (see [errors](learn/errors.md)) |
| `Error` | message of the last problem |
| `Event` | inside `On`: what happened |
| `ON`, `OFF`, `TRUE`, `FALSE` | switch values |
| `Nothing` | no value |

## Built-in helpers

| Helper | Result |
|---|---|
| `Length(X)`, `Count(X)` | characters in text, or items in a list |
| `Upper(X)`, `Lower(X)`, `Trim(X)` | changed text |
| `Number(X)`, `Text(X)` | convert |
| `Round(X)`, `Round(X, 2)` | rounded number |
| `Contains(X, Y)` | `ON` when X contains Y |
| `Replace(X, Old, New)` | text with replacements |
| `Split(X, ",")`, `Join(L, ", ")` | text to list, list to text |
| `List(A, B, C)` | a list |
| `Type(X)` | `Number`, `Text`, `Switch`, `List`, `Map` or `Nothing` |
| `Json(X)` | JSON text as a value |
| `Get(X, Key)` | the same as `X #Key` |

With `Import Math` these work too: `Sqrt`, `Abs`, `Floor`, `Ceil`, `Min`,
`Max`, `Sin`, `Cos`, `Tan`, `Log`, `Pow`.

## How values behave

- In a condition, these count as false: `OFF`, `0`, empty text, `Nothing`,
  an empty list, and the texts `off`, `false` and `no`.
- A number and a text that looks like the same number are equal.
- A thing (pin, item) used in a calculation or in text stands for its
  current value.
