# The checker

The checker reads a program without running it and reports what is wrong
or risky. `jadivcode run` uses it automatically; `jadivcode check` shows
everything, including tips.

```bash
jadivcode check program.jdv
```

```text
program.jdv:1: error E331: There is no library called 'Mth'
  hint: Did you mean 'Math'?
  fix available: Change to Math
program.jdv:3: warning S001: A secret ('ApiToken') is written directly in the program
  hint: Anyone who can read the file can read it. Keep it outside the program: ...
program.jdv: 1 error(s), 1 warning(s), 0 tip(s).
```

## Three levels

| Level | Meaning | Does the program start? |
|---|---|---|
| error | The line cannot work | No |
| warning | It works, but probably not as intended, or it is unsafe | Yes |
| info | A tip | Yes |

## Automatic fixes

```bash
jadivcode check --fix program.jdv
```

fixes misspelled keywords, names and libraries, adds missing `Import`
lines, closes a block that has no `End` and changes `http://` to
`https://`. The file is changed in place, so keep a copy when you are
unsure.

## Mistakes

| Code | Finding |
|---|---|
| `E101` | Text is missing its closing quote |
| `E201` | `End` without a block |
| `E202` | A block is never closed with `End` |
| `E240` | A line that cannot be understood |
| `E301` | A name that is not defined |
| `E303` | A value in `{ }` that cannot be understood |
| `E320`, `E321` | Unknown function, wrong number of values |
| `E330` | A library is used but not imported |
| `E331` | A library that does not exist |
| `E341` | A `Wait` time that is not valid |
| `E346` | `On` is used with something that is not an event |
| `E437` | A GPIO pin number outside 0 to 27 |
| `W101` | A value is treated as text because a name in it is not defined |
| `W102` | A name is defined but never used |
| `W103` | A new name looks like a misspelling of an existing one |
| `W110` | An endless loop without a pause |

## Safety findings

| Code | Finding | What to do |
|---|---|---|
| `S001` | A password, token or key is written in the program | Read it with `{System Env "NAME"}` |
| `S002` | Data is sent over unencrypted `http://` | Use `https://` |
| `S003` | A web page or webhook server is open to the network without protection | Set a `Password` or `Token` |
| `S004` | A value is pasted into a command line | Pass it as a separate value |
| `S005` | A file name comes from outside the program | Check the name before using it |
| `S006` | A secret is printed on screen | Remove the line |

Each finding is explained in [writing safe programs](../security.md).

The checker is a helper, not a guarantee. A program without findings can
still be wrong or unsafe.
