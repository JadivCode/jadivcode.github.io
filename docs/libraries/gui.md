# GUI

Desktop windows with buttons, text, inputs, checkboxes and sliders.

```text
Import GUI
```

Windows need Tk: `sudo apt install python3-tk`. Without a screen the
windows are simulated and every change is printed.

## A complete example

```text
Import GUI

Define Window = GUI Window #1
Define WindowWrite = GUI Write {} on Window #1
Define WindowSet = GUI Set {} on Window #1
Define ButtonPress = GUI Read Button {} on Window #1

WindowSet Title = Test app
WindowSet Size = 320x160
Start Window

WindowWrite Text "X = 20, Y = 20" "T01" = Press the button
WindowWrite Button "X = 20, Y = 60" "B01" = Press me

On ButtonPress "B01" "WindowWrite Text "T01" = Pressed"
```

The three `Define ... {}` lines are [shortcuts](../learn/libraries.md#shortcuts).
You can always write the long form instead:
`GUI Write Text "T01" on Window #1 = Hello`.

## Putting items in a window

```text
WindowWrite <Kind> "<position>" "<id>" = <text or value>
```

- **Kind**: `Text`, `Button`, `Input`, `Checkbox`, `Slider` or `Image`.
- **Position** (optional): `"X = 10, Y = 20"`, measured in pixels from the
  top left corner. Add `W` and `H` for a width and height:
  `"X = 10, Y = 20, W = 200, H = 30"`. Without a position, items are
  stacked from top to bottom.
- **Id**: your own name for the item, such as `"B01"`. Writing to an id
  that already exists changes that item.

| Kind | The value after `=` is |
|---|---|
| `Text` | the text shown |
| `Button` | the label |
| `Input` | the text in the box |
| `Checkbox` | the label |
| `Slider` | the position (0 to 100) |
| `Image` | the path of a PNG or GIF file |

## Changing the window and its items

```text
WindowSet Title = My app          // the window
WindowSet "T01" Color = red       // one item
```

| Window property | Example |
|---|---|
| `Title` | `My app` |
| `Size` | `400x300` |
| `Width`, `Height` | `400` |
| `Color` | `white`, `#202020` |

| Item property | Meaning |
|---|---|
| `Text` | text or label |
| `Value` | content of an input, checkbox (`ON`/`OFF`) or slider |
| `Color`, `Background` | a color name or `#rrggbb` |
| `Size` | text size |
| `Enabled` | `OFF` greys the item out |
| `X`, `Y`, `W`, `H` | position and size |
| `Min`, `Max` | range of a slider (set before the window starts) |

## Reading and reacting

```text
Define WindowRead = GUI Read Input {} on Window #1
Write = {WindowRead "I01"}
```

| Read | As a value | As an event (`On`) |
|---|---|---|
| `Read Button "B01"` | `ON` if it was the last button pressed | a click; `{Event}` is the id |
| `Read Input "I01"` | the typed text | Enter was pressed; `{Event}` is the text |
| `Read Checkbox "C01"` | `ON` or `OFF` | it was toggled |
| `Read Slider "S01"` | the position | it was moved |

Leave out the id in an event to react to every item of that kind.

## Other commands

| Command | Meaning |
|---|---|
| `Start Window`, `Stop Window` | show, close |
| `GUI Remove "T01" on Window #1` | remove an item |
| `GUI Press "B01" on Window #1` | click a button from the program |

The program keeps running until every window is closed.
