# Command line

Everything is done with the `jadivcode` command.

| Command | What it does |
|---|---|
| `jadivcode run file.jdv` | Check the program, then run it |
| `jadivcode file.jdv` | The same, shorter |
| `jadivcode check file.jdv` | Find mistakes and unsafe code without running |
| `jadivcode new name` | Create `name.jdv` from a template |
| `jadivcode libs` | List the libraries |
| `jadivcode libs GUI` | Show every command of one library |
| `jadivcode repl` | Try statements one at a time |
| `jadivcode explain file.jdv` | Ask the optional [AI helper](ai.md) |
| `jadivcode ide` | Open the [JadivCode IDE](ide.md), when it is installed |
| `jadivcode --version` | Show the installed version |

## run

```bash
jadivcode run program.jdv
jadivcode run program.jdv first second    # values for {System Args}
```

| Option | Meaning |
|---|---|
| `--sim` | Simulate GPIO pins and GUI windows |
| `--strict` | Stop at the first problem |
| `--quiet` | Do not show checker warnings |
| `--force` | Run even though the checker found errors |

The command ends with code `0` when the program ran, and `1` when it could
not start or was stopped by an error.

## check

```bash
jadivcode check program.jdv
jadivcode check --fix program.jdv     # repair what can be repaired
jadivcode check --json program.jdv    # for editors and other tools
```

The command ends with code `1` when it found at least one error.

## repl

```text
$ jadivcode repl
jdv> Define A = 5
jdv> Write = {A * 2}
10
jdv> Exit
```

## Environment variables

| Variable | Meaning |
|---|---|
| `JADIVCODE_GPIO` | `sim` forces simulated pins, `real` refuses to run without hardware |
| `JADIVCODE_GUI` | `headless` forces simulated windows |
| `JADIVCODE_AI_MODEL` | Model used by `jadivcode explain` |
