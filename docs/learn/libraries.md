# 7. Libraries and shortcuts

Libraries add abilities to the language. Bring one in with `Import` at the
top of the program:

```text
Import Math
Import GPIO
```

List every library and its commands in the terminal:

```bash
jadivcode libs
jadivcode libs GUI
```

## Three ways to use a library

**1. Get a value** inside `{ }`:

```text
Write = {Math "5x5"}
Write = It is {Time Now}
```

**2. Do something** with a statement:

```text
GPIO Write #17 = ON
File Write "notes.txt" = Remember the milk
```

**3. Create a thing** and give it a name:

```text
Define Lamp = GPIO #17
Define Go = GUI Button "Press me"
```

A named thing is then used like any other value:

```text
Set Lamp = ON
If Lamp = ON then Write = The lamp is on
```

The `#` sign gives a thing its number: pin 17, window 1, port 8090.

## Things

A named thing keeps working after it is created. Every thing understands
the same few statements:

| Statement | Meaning | Example |
|---|---|---|
| `Set Name = value` | change it | `Set Lamp = ON`, `Set Hello = New text` |
| `Set Name Property = value` | change one property | `Set Hello Color = red` |
| `{Name}` | read it | `{Lamp}`, `{Field}` |
| `On Name` | react to it | `On Go "Write = click"` |
| `Start Name`, `Stop Name` | start, stop or remove it | `Stop Server` |

## Shortcuts

Some library commands are long. `Define` can turn the fixed part into a
shortcut. Put `{}` where the changing part goes:

```text
Define Hook = Web Read Hook {} on Server #8090
```

Now the same command is shorter:

```text
On Hook "/lamp" "Write = lamp"
On Hook "/door" "Write = door"
```

A shortcut works wherever the long command works: as a statement, inside
`{ }` and after `On`.

Next: [events](events.md).
