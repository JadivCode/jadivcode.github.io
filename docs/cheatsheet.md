# Cheat sheet

The whole language on one page.

## Basics

| Write this | To do this |
|---|---|
| `// note` | A comment |
| `Write = Hello {Name}` | Show text; `{ }` inserts a value |
| `Ask Name = Your name?` | Ask a question and store the answer |
| `Define Count = 0` | Create a value |
| `Set Count = Count + 1` | Change a value |
| `Wait 5s` | Pause (`ms`, `s`, `m`, `h`) |
| `Stop` | End the program |
| `Import Math` | Use a library |

## Decisions

```text
If Count > 3 then Write = big else Write = small

If Count > 3
    Write = big
Else If Count = 3
    Write = exactly three
Else
    Write = small
End
```

Compare with `=` `!=` `<` `>` `<=` `>=` `is` `is not`. Combine with `and`
`or` `not`.

## Loops

```text
Repeat 3 times ... End
For I = 1 to 10 ... End
For I = 10 to 0 step -2 ... End
For each Item in Items ... End
While Count < 10 ... End
Forever ... End
```

`Break` leaves a loop. `Continue` starts the next round.

## Lists

| Write this | To do this |
|---|---|
| `Define L = List 1, 2, 3` | Create a list |
| `Add 4 to L` | Add an item |
| `Remove 2 from L` | Remove an item |
| `{L #1}` | Read the first item |
| `{Length(L)}` | Count the items |

## Functions

```text
Function Greet Name
    Write = Hello, {Name}
End
Call Greet "Jan"

Function Double N
    Return N * 2
End
Write = {Double(21)}
```

## Libraries and things

| Write this | To do this |
|---|---|
| `Define Lamp = GPIO #17` | Create a named thing |
| `Define Go = GUI Button "Press me" at 20, 60` | Create a window item |
| `Set Lamp = ON` | Change it |
| `Set Go Color = red` | Change one property |
| `{Lamp}` | Read it |
| `On Go "Write = click"` | React to it |
| `Start Server`, `Stop Server` | Start, stop or remove it |
| `Define Hook = Web Read Hook {} on Server #8090` | Make a shortcut; `{}` is the changing part |

## Events

```text
On Go "Write = pressed"

On Go
    Write = pressed {Event}
End
```

## Problems

| Write this | To do this |
|---|---|
| `{Success}` | `Full`, `Partial` or `None` |
| `{Error}` | Message of the last problem |
| `Strict ON` | Stop at the first problem |

## Helpers

`Length` `Upper` `Lower` `Trim` `Number` `Text` `Round` `Contains`
`Replace` `Split` `Join` `Type` `Json` `Get`

## Reserved words

These cannot be used as names:

`Import` `Define` `Set` `Write` `Ask` `Wait` `If` `Then` `Else` `End`
`Repeat` `While` `Forever` `For` `Function` `Return` `Call` `On` `Start`
`Stop` `Exit` `Break` `Continue` `Strict` `Add` `Remove` `And` `Or` `Not`
`Is` `ON` `OFF` `True` `False` `Nothing`
