# Math

Calculations written the way you write them on paper.

```text
Import Math
```

## Written calculations

```text
Write = {Math "5x5"}              // 25
Write = {Math "(2 + 3) x 4"}      // 20
Write = {Math "10 ÷ 4"}           // 2.5
Write = {Math "2 ^ 10"}           // 1024
Write = {Math "sqrt(16) + 1"}     // 5
```

Inside the quotes you may use `x` or `×` for multiplying, `÷` or `/` for
dividing, `^` for powers, round brackets, your own names, `pi` and `e`,
and these functions: `sqrt`, `abs`, `floor`, `ceil`, `min`, `max`, `sin`,
`cos`, `tan` (angles in degrees), `log` and `pow`.

```text
Define Radius = 3
Write = Area: {Math "pi x Radius ^ 2"}
```

!!! tip
    The ordinary signs `+ - * / % ^` work everywhere without the Math
    library: `{Width * Height}`.

## Commands

| Command | Result |
|---|---|
| `{Math Round 3.14159 2}` | `3.14` (leave out the 2 for a whole number) |
| `{Math Floor 3.7}`, `{Math Ceil 3.2}` | `3`, `4` |
| `{Math Abs -5}` | `5` |
| `{Math Sqrt 16}` | `4` |
| `{Math Power 2 8}` | `256` |
| `{Math Mod 10 3}` | `1` |
| `{Math Min 4 9 2}`, `{Math Max 4 9 2}` | `2`, `9` |
| `{Math Sum 1 2 3}`, `{Math Average 1 2 3}` | `6`, `2` |
| `{Math Random 1 6}` | a whole number from 1 to 6 |
| `{Math Random}` | a number between 0 and 1 |
| `{Math Random Colors}` | a random item of a list |
| `{Math Sin 90}`, `{Math Cos 0}`, `{Math Tan 45}` | `1`, `1`, `1` |
| `{Math Pi}` | `3.14159...` |

`Min`, `Max`, `Sum` and `Average` also accept a list: `{Math Sum Prices}`.
