# 1. Your first program

A JadivCode program is a text file whose name ends in `.jdv`.

## Create and run

Create a file called `hello.jdv` with any text editor and type:

```text
Write = Hello, world!
```

Run it in a terminal:

```bash
jadivcode run hello.jdv
```

```text
Hello, world!
```

`Write` shows text on the screen. Everything after `=` is shown.

!!! tip
    `jadivcode new hello` creates a starter file for you.

## More lines

A program runs from the top line to the bottom line, one line at a time.

```text
Write = Getting ready...
Wait 2s
Write = Done.
```

`Wait` pauses the program. You can write `2s` (seconds), `500ms`
(milliseconds), `3m` (minutes) or `1h` (hours).

## Comments

Text after `//` is a note for people. JadivCode ignores it.

```text
// This program greets the world.
Write = Hello!   // this note is ignored too
```

## Capital letters do not matter

These three lines do the same thing:

```text
Write = hi
write = hi
WRITE = hi
```

## Ask a question

```text
Ask Name = What is your name?
Write = Nice to meet you, {Name}.
```

`Ask` shows the question and stores the answer under the name `Name`.
Curly braces `{ }` inside text are replaced by a value.

Next: [values and text](values.md).
