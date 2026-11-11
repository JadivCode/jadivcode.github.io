# Writing safe programs

A JadivCode program can switch real devices, read files and talk to the
network. These habits keep it from doing harm. The
[checker](tools/checker.md) warns about each of them.

## Keep secrets out of the program (S001, S006)

Passwords, tokens, API keys and webhook addresses do not belong in a
`.jdv` file. Files get copied, shared and uploaded.

```text
// Unsafe
Define Token = abc123

// Safe
Import System
Define Token = {System Env "API_TOKEN"}
```

```bash
API_TOKEN="abc123" jadivcode run program.jdv
```

Do not `Write` a secret either. Whatever is shown on screen ends up in
logs and screenshots.

## Use https (S002)

Everything sent to an `http://` address can be read by anyone between you
and the server. Use `https://` whenever the other side offers it.
Addresses inside your own network (`192.168.x.x`, `localhost`, names
ending in `.local`) are not reported.

## Do not open services without protection (S003)

A WebUI page and a Web Server listen only on your own computer by default.
When you change `Host` to let other devices in, add a password or token:

```text
PageSet Host = 0.0.0.0
PageSet Password = {System Env "PAGE_PASSWORD"}
```

```text
Set Server Host = 0.0.0.0
Set Server Token = {System Env "HOOK_TOKEN"}
```

Do not forward these ports to the internet. Use a VPN or an HTTPS reverse
proxy when you need access from outside.

## Do not paste values into commands (S004)

```text
// Unsafe: an answer like "-rf /home" changes what the command does
Write = {System Run "ls {Folder}"}

// Safe: the value is always exactly one argument
Write = {System Run "ls" Folder}
```

## Check file names that come from outside (S005)

A file name typed by a user or received from the network can point
anywhere, for example `../../etc/passwd`.

```text
Ask Name = Which note?
If Contains(Name, "/") or Contains(Name, "..") then Stop
Write = {File Read "notes/{Name}.txt"}
```

## Treat received data as untrusted

Whatever arrives through `Ask`, a web page input or a webhook was written
by someone else. Check that it is what you expect before acting on it:

```text
On Hook "/lamp"
    If {Event #"state"} = "on" then Set Lamp = ON
    If {Event #"state"} = "off" then Set Lamp = OFF
End
```

## Pause in endless loops (W110)

A loop without `Wait` keeps a processor core at 100 percent, which heats a
Raspberry Pi and slows everything else.

## Hardware

Software cannot protect a wrongly wired circuit. Check voltages and
currents before you connect anything to a pin, and read the warning on the
[GPIO page](libraries/gpio.md).
