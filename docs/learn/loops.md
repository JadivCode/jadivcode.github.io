# 4. Loops

A loop runs the same lines several times. Every loop ends with `End`.

## A fixed number of times

```text
Repeat 3 times
    Write = Hello
End
```

## Counting

```text
For I = 1 to 5
    Write = Number {I}
End
```

Count in bigger steps, or backwards, with `step`:

```text
For I = 10 to 0 step -2
    Write = {I}
End
```

## While something is true

```text
Define Count = 0
While Count < 3
    Set Count = Count + 1
    Write = Count is {Count}
End
```

## Forever

```text
Forever
    Write = tick
    Wait 1s
End
```

Stop a program that runs forever with ++ctrl+c++.

!!! warning "Always pause in an endless loop"
    A loop that never waits uses a whole processor core. Put a `Wait`
    inside, even a short one such as `Wait 100ms`.

## Leaving early

- `Break` leaves the loop.
- `Continue` jumps to the next round.
- `Stop` ends the whole program.

```text
For I = 1 to 10
    If I = 3 then Continue
    If I = 6 then Break
    Write = {I}
End
```

This writes 1, 2, 4 and 5.

Next: [lists](lists.md).
