# JadivCode

**A super simple programming language for Linux.** Programs read almost
like sentences and run with one command.

```text
Import GPIO
Import Math

Define Lamp = GPIO #17
Set Lamp = ON
Wait 5s
Set Lamp = OFF

Write = The answer is {Math "5x5"}
If Success = "Full" then "Write = OK" else "Write = ERROR"
```

```bash
jadivcode run lamp.jdv
```

## What you can do with it

| | |
|---|---|
| **Switch hardware** | Raspberry Pi pins with the [GPIO](libraries/gpio.md) library. On a PC the pins are simulated, so you can learn without hardware. |
| **Open windows** | Buttons, text, inputs and sliders with the [GUI](libraries/gui.md) library. |
| **Serve web pages** | The same items in a browser with [WebUI](libraries/webui.md), usable from a phone. |
| **Talk to other systems** | Call and receive webhooks (for example Home Assistant) with [Web](libraries/web.md). |
| **Calculate** | Write maths the way you write it on paper with [Math](libraries/math.md). |

## Why it is easy

- **One statement per line.** No brackets, semicolons or indentation rules.
- **Not case sensitive.** `Write`, `write` and `WRITE` are the same.
- **Helpful mistakes.** A misspelled word gets a "Did you mean ...?" answer,
  and many mistakes can be repaired with `jadivcode check --fix`.
- **Safety checks built in.** JadivCode warns when a program contains a
  password, sends data unencrypted or opens itself to the network.

## Start here

1. [Install JadivCode](install.md)
2. [Write your first program](learn/first-program.md)
3. Keep the [cheat sheet](cheatsheet.md) open while you learn

JadivCode runs on Linux and is free software under the Apache License 2.0.
