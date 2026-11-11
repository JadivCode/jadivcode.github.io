# 8. Events

An event is something that happens while the program runs: a button is
clicked, a pin changes, a webhook arrives. `On` tells JadivCode what to do
when it happens.

## One line

```text
Import GUI

Define Window = GUI Window #1
Define WindowWrite = GUI Write {} on Window #1
Define ButtonPress = GUI Read Button {} on Window #1
Start Window

WindowWrite Button "X = 10, Y = 10" "B01" = Press me
On ButtonPress "B01" "WindowWrite Text "X = 10, Y = 50" "T01" = Pressed"
```

The line reads: *on a press of button B01, run the statement in quotes.*
Leave out `"B01"` to react to every button.

You may add `Else loop` at the end to say "otherwise keep waiting". It is
optional, because waiting is what JadivCode does anyway.

## Several lines

```text
Define Clicks = 0

On ButtonPress "B01"
    Set Clicks = Clicks + 1
    WindowWrite Text "T01" = Pressed {Clicks} times
End
```

## The Event value

Inside `On`, the name `Event` holds what happened: the id of the button,
the text that was typed, the state of a pin or the data of a webhook.

```text
Define Typed = GUI Read Input {} on Window #1
On Typed "I01" "Write = You typed {Event}"
```

## When does the program end?

A program with an open window, a running web page or a webhook server keeps
running after its last line and waits for events. It ends when the window
is closed, when a `Stop` statement runs, or when you press ++ctrl+c++.

## Events from other libraries

| Event | Example |
|---|---|
| A pin changes | `On Button Pressed "Write = click"` ([GPIO](../libraries/gpio.md)) |
| A web page button | `On Click "B01" "Set Lamp = ON"` ([WebUI](../libraries/webui.md)) |
| A webhook arrives | `On Hook "/lamp" "Write = {Event}"` ([Web](../libraries/web.md)) |

Next: [when things go wrong](errors.md).
