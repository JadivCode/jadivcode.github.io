# 6. Functions

A function is a named group of lines that you can run whenever you need it.

## Without a result

```text
Function Greet Name
    Write = Hello, {Name}!
End

Call Greet "Jan"
Call Greet "Veronika"
```

The names after the function name (`Name` here) receive the values given
to `Call`. Separate several values with commas:

```text
Function Introduce Name, City
    Write = {Name} lives in {City}
End

Call Introduce "Jan", "Piconcillo"
```

## With a result

`Return` hands a value back. Use the function inside `{ }` or after `=`,
with the values in round brackets:

```text
Function Double N
    Return N * 2
End

Write = {Double(21)}
Set Total = Double(5) + 1
```

## Good to know

- A function must be defined above the line that first uses it.
- Names created inside a function exist only inside it. Names from the
  main program can be read and changed inside a function.

Next: [libraries and shortcuts](libraries.md).
