# 8. Events

An event is something that happens while the program runs: a button is
clicked, a pin changes, a webhook arrives. `On` tells JadivCode what to do
when it happens.

## One line

```text
Import GUI

Define Message = GUI Text "Press the button" at 20, 20
Define Go = GUI Button "Press me" at 20, 60

On Go "Set Message = Pressed"
```

The last line reads: *when Go is used, run the statement in quotes.*

You may add `Else loop` at the end to say "otherwise keep waiting". It is
optional, because waiting is what JadivCode does anyway.

## Several lines

```text
Define Clicks = 0

On Go
    Set Clicks = Clicks + 1
    Set Message = Pressed {Clicks} times
End
```

## The Event value

Inside `On`, the name `Event` holds what happened: the text that was
typed, the new state of a pin, the data of a webhook.

```text
Define Field = GUI Input at 20, 100
On Field "Set Message = You typed {Event}"
```

## When does the program end?

A program with an open window, a running web page or a webhook server keeps
running after its last line and waits for events. It ends when the window
is closed, when a `Stop` statement runs, or when you press ++ctrl+c++.

## What can be used with On

| Thing | Example |
|---|---|
| A window or web page item | `On Go "Write = click"` ([GUI](../libraries/gui.md), [WebUI](../libraries/webui.md)) |
| An input pin | `On Button Pressed "Write = click"` ([GPIO](../libraries/gpio.md)) |
| A webhook | `On Hook "/lamp" "Write = {Event}"` ([Web](../libraries/web.md)) |

Next: [when things go wrong](errors.md).
