# GUI

Desktop windows with texts, buttons, inputs, checkboxes and sliders.

```text
Import GUI
```

Windows need Tk: `sudo apt install python3-tk`. Without a screen the
windows are simulated and every change is printed.

## A complete example

```text
Import GUI

GUI Title = Counter
GUI Size = 260x150

Define Message = GUI Text "Count: 0" at 20, 20
Define Add = GUI Button "Add one" at 20, 70

Define Count = 0
On Add
    Set Count = Count + 1
    Set Message = Count: {Count}
End
```

Every item gets a **name** (`Message`, `Add`). You then use the name like
any other value: `Set` changes it, `{Name}` reads it, `On` reacts to it.

The window opens by itself as soon as the program has nothing else to do,
and the program runs until the window is closed.

## Creating items

```text
Define <Name> = GUI <Kind> <text or value> at <x>, <y> size <width>, <height>
```

| Kind | Example | The value is |
|---|---|---|
| `Text` | `Define Hello = GUI Text "Hello" at 20, 20` | the text shown |
| `Button` | `Define Go = GUI Button "Press me" at 20, 60` | the label |
| `Input` | `Define Field = GUI Input at 20, 100 size 200, 28` | the text in the box (optional) |
| `Checkbox` | `Define Agree = GUI Checkbox "I agree" at 20, 140` | the label |
| `Slider` | `Define Level = GUI Slider 50 at 20, 180` | the position, 0 to 100 |
| `Image` | `Define Logo = GUI Image "logo.png" at 20, 230` | a PNG or GIF file |

- `at x, y` is the position in pixels from the top left corner.
- `size width, height` is optional.
- Without `at`, items are stacked from top to bottom.

## Changing items

```text
Set Hello = New text          // text, label or value
Set Hello Color = red         // one property
Stop Hello                    // remove the item
```

| Property | Meaning |
|---|---|
| `Text` | text or label |
| `Value` | content of an input, checkbox (`ON` / `OFF`) or slider |
| `Color`, `Background` | a color name or `#rrggbb` |
| `Size` | text size |
| `Enabled` | `OFF` greys the item out |
| `X`, `Y`, `W`, `H` | position and size |
| `Min`, `Max` | range of a slider |

## Reading items

`{Name}` gives what the item holds:

| Kind | `{Name}` is |
|---|---|
| `Text`, `Button` | its text |
| `Input` | what the user typed |
| `Checkbox` | `ON` or `OFF` |
| `Slider` | its position |

```text
On Go
    Write = You typed {Field} and the slider is at {Level}
End
```

## Reacting to items

| `On` an item of kind | Runs when | `{Event}` is |
|---|---|---|
| `Button` | it is clicked | the name of the button |
| `Input` | Enter is pressed in it | the typed text |
| `Checkbox` | it is toggled | `ON` or `OFF` |
| `Slider` | it is moved | the new position |

```text
On Field "Set Hello = You typed {Event}"

On Level
    Set Hello = Slider at {Event}
End
```

`GUI Press "Go"` clicks an item from the program.

## The window

| Line | Meaning |
|---|---|
| `GUI Title = My app` | title bar text |
| `GUI Size = 400x300` | width x height in pixels |
| `GUI Width = 400`, `GUI Height = 300` | one side only |
| `GUI Color = white` | background color |

## More than one window

Give further windows a name and add `on Window #2` to their items:

```text
Define Second = GUI Window #2
Set Second Title = Settings
Define Close = GUI Button "Close" at 20, 20 on Window #2

On Close "Stop Second"
```

`Start Second` shows a window immediately and `Stop Second` closes it.

## A calculator

```text
Import GUI
Import Math

GUI Title = Calculator
GUI Size = 320x150

Define Hint = GUI Text "Type a calculation and press Enter:" at 20, 15
Define Field = GUI Input at 20, 45 size 220, 28
Define Result = GUI Text "" at 20, 90

On Field
    Define Answer = {Math Event}
    If Success = "None"
        Set Result = That is not a calculation
    Else
        Set Result = {Event} = {Answer}
    End
End
```

## Long form (by id)

Items can also be created and used by an id in quotes, without names.
Programs written for the first version of JadivCode use this form, and it
keeps working.

| Long form | Meaning |
|---|---|
| `GUI Write Button "X = 10, Y = 10" "B01" on Window #1 = Press me` | create or change an item |
| `GUI Set "B01" Color on Window #1 = red` | change a property |
| `GUI Set Title on Window #1 = My app` | change the window |
| `{GUI Read Input "I01" on Window #1}` | read an item |
| `On GUI Read Button "B01" on Window #1 "Write = pressed"` | an event |
| `GUI Remove "B01" on Window #1` | remove an item |

The position string accepts `X`, `Y`, `W` and `H`. A long form can be
shortened with a [shortcut](../learn/libraries.md#shortcuts):

```text
Define WindowWrite = GUI Write {} on Window #1
WindowWrite Button "X = 10, Y = 10" "B01" = Press me
```

!!! tip "Design windows with the mouse"
    The [JadivCode IDE](../tools/ide.md#designers) has a designer that
    writes these lines for you.
