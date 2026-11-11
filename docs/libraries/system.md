# System

Run other programs and read information about the computer.

```text
Import System
```

```text
Write = Kernel: {System Run "uname -r"}
Write = Home folder: {System Env "HOME"}
```

| Command | Meaning |
|---|---|
| `{System Run "command"}` | run a program and get what it printed |
| `System Run "command"` | run a program and show what it printed |
| `{System Env "NAME"}` | an environment variable (empty when not set) |
| `{System Args}` | list of values given after the file name |
| `{System Platform}` | for example `Linux aarch64` |
| `{System User}` | name of the current user |

## Passing values to a program

Give changing values as **separate values after the command**, not inside
the quotes:

```text
Ask Folder = Which folder?
Write = {System Run "ls -l" Folder}
```

Each extra value reaches the program as exactly one argument, even when it
contains spaces or special characters.

`System Run` starts the program directly, without a shell. Shell features
such as `|`, `>` and `*` therefore do not work, and they cannot be abused
either. A program that takes longer than 5 minutes is stopped.

## Values from the command line

```bash
jadivcode run greet.jdv Jan Veronika
```

```text
Import System
For each Name in {System Args}
    Write = Hello, {Name}
End
```
