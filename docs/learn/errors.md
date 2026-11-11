# 9. When things go wrong

## Before the program starts

`jadivcode run` checks the whole program first. If a line cannot be
understood, nothing runs and you see where the problem is:

```text
hello.jdv:2: error E240: I do not understand 'Wrte = hello'
  hint: Did you mean 'Write'?
  fix available: Change to Write
```

Let JadivCode repair what it can:

```bash
jadivcode check --fix hello.jdv
```

See [the checker](../tools/checker.md) for everything it finds.

## While the program runs

Some problems only appear while running: a file is missing, a web address
does not answer, a number is divided by zero. JadivCode then:

1. shows a warning with the line number,
2. skips that line,
3. continues with the next line.

Two built-in names tell the program what happened:

| Name | Value |
|---|---|
| `Success` | `Full` when every line so far worked, `None` when the line just before failed, `Partial` when an earlier line failed |
| `Error` | the message of the last problem |

```text
Import Web

Web Get "https://example.com/data"
If Success = "Full" then "Write = OK" else "Write = Failed: {Error}"
```

## Strict mode

When a program must not continue after a problem, turn on strict mode:

```text
Strict ON
```

or run it with:

```bash
jadivcode run --strict program.jdv
```

In strict mode the first problem stops the program.

## Getting help from the AI helper

`jadivcode explain program.jdv` asks an AI model to explain the problems
and show a corrected program. It is optional and off by default. See
[AI helper](../tools/ai.md).
