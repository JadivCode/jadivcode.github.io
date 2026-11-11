# GPIO

Switch and read the pins of a Raspberry Pi.

```text
Import GPIO
```

Pins use **BCM numbers** (the "GPIO17" numbers printed on pinout charts),
from 0 to 27. They are not the physical positions on the header.

!!! note "No Raspberry Pi? No problem"
    On a computer without GPIO hardware every pin is simulated and each
    change is printed, for example `[GPIO simulator] pin 17 -> ON`. Force
    the simulator anywhere with `jadivcode run --sim program.jdv`.

    For real pins install: `sudo apt install python3-gpiozero python3-lgpio`

!!! danger "Protect your hardware"
    A Raspberry Pi pin works at 3.3 V and can supply only a few
    milliamps. Never connect 5 V to a pin, and drive motors, relays and
    LED strips through a transistor or driver board.

## Outputs

```text
Define Lamp = GPIO #17
Set Lamp = ON
Wait 2s
Set Lamp = OFF
```

A pin becomes an output the first time you `Set` it. Read its state with
`{Lamp}`.

## Inputs

```text
Define Button = GPIO Input #4 PullUp
If Button = ON then Write = The button is pressed
```

`PullUp` or `PullDown` switches on the pin's internal resistor. Leave it
out when your circuit has its own resistor.

## Reacting to an input

```text
Define Button = GPIO Input #4 PullDown
Define Lamp = GPIO #17

On Button Pressed
    Set Lamp = ON
End
On Button Released "Set Lamp = OFF"
```

Events: `Pressed`, `Released`, `Changed`. Inside `On`, `{Event}` is the new
state.

## Dimming (PWM)

```text
Define Fan = GPIO PWM #18
Set Fan = 40      // 40 percent
Set Fan = OFF     // 0 percent
```

## All commands

| Command | Meaning |
|---|---|
| `Define X = GPIO #17` | A pin; output when set, input when read |
| `Define X = GPIO Output #17` | An output pin |
| `Define X = GPIO Input #4` | An input pin (add `PullUp` or `PullDown`) |
| `Define X = GPIO PWM #18` | A dimmable output, 0 to 100 |
| `Set X = ON` | Switch a pin |
| `{X}` | State of a pin |
| `GPIO Write #17 = ON` | Switch a pin without a name |
| `{GPIO Read #4}` | Read a pin without a name |
| `On X Pressed "..."` | React to an input |
| `Stop X` | Release a pin |
| `{GPIO Mode}` | `real` or `sim` |
| `GPIO Simulate #4 = ON` | Simulator only: pretend an input changed |
