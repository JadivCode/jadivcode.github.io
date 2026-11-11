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
Define Page = WebUI Page #1
Define PageWrite = WebUI Write {} on Page #1
Define PageSet = WebUI Set {} on Page #1
Define Click = WebUI Read Button {} on Page #1

PageSet Title = Lamp panel
PageSet Port = 8080
Start Page

PageWrite Text "T01" = The lamp is OFF
PageWrite Button "B01" = Toggle lamp

On Click "B01"
    If Lamp = ON then Set Lamp = OFF else Set Lamp = ON
    PageWrite Text "T01" = The lamp is {Lamp}
End
```

Run it and open <http://localhost:8080/>. The page updates by itself when
the program changes an item.

`Write`, `Set`, `Read`, `Remove` and `Press` work exactly as in
[GUI](gui.md). Positions are optional; without them items are placed from
top to bottom, which suits phones best.

## Page properties

| Property | Meaning | Default |
|---|---|---|
| `Title` | heading and browser tab title | `JadivCode` |
| `Port` | port of the web server | `8080` |
| `Host` | who may connect | `127.0.0.1` (this computer only) |
| `Password` | password asked by the browser | none |
| `Color` | page background | |

Set `Port`, `Host` and `Password` before `Start Page`.

## Opening the page to your network

By default only the computer running the program can open the page. To
use it from a phone, allow other devices **and set a password**:

```text
Import System

PageSet Host = 0.0.0.0
PageSet Password = {System Env "PAGE_PASSWORD"}
Start Page
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

The program keeps running until the page is stopped (`Stop Page`) or you
press ++ctrl+c++.
