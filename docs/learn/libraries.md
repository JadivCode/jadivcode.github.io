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
Define Window = GUI Window #1
```

A named thing is then used like any other value:

```text
Set Lamp = ON
Start Window
If Lamp = ON then Write = The lamp is on
```

The `#` sign gives a thing its number: pin 17, window 1, port 8090.

## Shortcuts

Some commands are long:

```text
GUI Write Button "X = 10, Y = 10" "B01" on Window #1 = Press me
```

`Define` can turn the fixed part into a shortcut. Put `{}` where the
changing part goes:

```text
Define WindowWrite = GUI Write {} on Window #1
```

Now the same command is shorter:

```text
WindowWrite Button "X = 10, Y = 10" "B01" = Press me
WindowWrite Text "X = 10, Y = 50" "T01" = Hello
```

Shortcuts work for getting values and for events too:

```text
Define WindowRead = GUI Read Input {} on Window #1
Write = You typed {WindowRead "I01"}
```

Next: [events](events.md).
