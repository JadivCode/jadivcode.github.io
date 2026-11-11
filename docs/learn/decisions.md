# 3. Decisions

## One line

```text
Ask Age = How old are you?
If Age >= 18 then Write = Welcome else Write = Too young
```

The part after `else` is optional. You may put each statement in quotes,
which is easier to read when the statement is long:

```text
If Age >= 18 then "Write = Welcome" else "Write = Too young"
```

## Several lines

When more than one thing should happen, write a block and finish it with
`End`:

```text
If Age >= 18
    Write = Welcome
    Write = Come in
Else If Age >= 16
    Write = Almost there
Else
    Write = Too young
End
```

Indenting the lines inside a block is optional, but it makes programs
easier to read.

## Comparing

| Written | True when |
|---|---|
| `A = B` or `A is B` | equal |
| `A != B` or `A is not B` | different |
| `A < B`, `A > B` | smaller, larger |
| `A <= B`, `A >= B` | smaller or equal, larger or equal |

Comparing text with `=` ignores capital letters, so `"Yes" = "yes"` is
true. Use `==` when capitals must match exactly.

## Combining

```text
If Age >= 18 and Age < 65 then Write = adult
If Day = "Saturday" or Day = "Sunday" then Write = weekend
If not Ready then Write = please wait
```

Next: [loops](loops.md).
