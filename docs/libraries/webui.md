# WebUI

The same items as [GUI](gui.md), shown as a web page. Open it in a
browser on the same computer, or from a phone.

```text
Import WebUI
```

## A complete example

```text
Import WebUI
Import GPIO

Define Lamp = GPIO #17

WebUI Title = Lamp panel
Define Status = WebUI Text "The lamp is OFF"
Define Toggle = WebUI Button "Toggle lamp"

On Toggle
    If Lamp = ON then Set Lamp = OFF else Set Lamp = ON
    Set Status = The lamp is {Lamp}
End
```

Run it and open <http://localhost:8080/>. The page updates by itself when
the program changes an item. The program runs until you press ++ctrl+c++.

## Items

Items are created, changed, read and used in events exactly as in
[GUI](gui.md); only the library name differs:

```text
Define Hello = WebUI Text "Hello"
Define Go = WebUI Button "Go"
Define Field = WebUI Input
Define Agree = WebUI Checkbox "I agree"
Define Level = WebUI Slider 50
Define Logo = WebUI Image "https://example.com/logo.png"
```

Items appear from top to bottom in the order they are defined, which suits
phones best. `at x, y` and `size w, h` are accepted when you want exact
positions.

An input reports its text when the user leaves the box or presses Enter.

## The page

| Line | Meaning | Default |
|---|---|---|
| `WebUI Title = My panel` | heading and browser tab title | `JadivCode` |
| `WebUI Port = 8080` | port of the web server | `8080` |
| `WebUI Host = 0.0.0.0` | who may connect | `127.0.0.1` (this computer only) |
| `WebUI Password = ...` | password asked by the browser | none |
| `WebUI Color = white` | page background | |

Set `Port`, `Host` and `Password` at the top of the program, before the
page starts.

## Opening the page to your network

By default only the computer running the program can open the page. To
use it from a phone, allow other devices **and set a password**:

```text
Import WebUI
Import System

WebUI Host = 0.0.0.0
WebUI Password = {System Env "PAGE_PASSWORD"}
```

Start the program with the password in the environment:

```bash
PAGE_PASSWORD="choose-a-long-one" jadivcode run panel.jdv
```

Then open `http://<address of the computer>:8080/`. The browser asks for a
user name and password; any user name works.

!!! warning
    The page is served over plain `http`. The password protects against
    casual access on a home network, not against someone who can listen
    to the network traffic. Do not expose it to the internet directly; put
    it behind a VPN or an HTTPS reverse proxy.

## Starting and stopping by hand

```text
Define Page = WebUI Page #1
Start Page
Stop Page
```

The long forms by id (`WebUI Write ...`, `WebUI Read ...`) work as
described for [GUI](gui.md#long-form-by-id), with `Page #1` in place of
`Window #1`.

!!! tip "Design pages with the mouse"
    The [JadivCode IDE](../tools/ide.md#designers) has a web page designer.
