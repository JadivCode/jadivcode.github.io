# Web

HTTP requests and incoming webhooks. Use it to talk to Home Assistant,
REST APIs and other programs.

```text
Import Web
```

## Getting data

```text
Write = {Web Get "https://example.com"}
```

For JSON, `Web Json` turns the answer into a value you can read with `#`:

```text
Define Data = {Web Json "https://api.example.com/weather"}
Write = Temperature: {Data #"temperature"}
```

## Sending data

```text
Web Post "https://example.com/notify" = The door is open
Web Json "https://example.com/api" = state: on, level: 50
```

`Web Json` sends `{"state": true, "level": 50}`. Write the fields as
`name: value`, separated by commas.

After a request:

| Value | Meaning |
|---|---|
| `{Web Status}` | status code of the last request (`200` means OK) |
| `{Web Reply}` | text of the last answer |
| `{Success}` | `Full` when it worked |

## Calling a Home Assistant webhook

```text
Import Web
Import System

Define Address = {System Env "HA_WEBHOOK"}
Web Json Address = state: on, source: jadivcode
If Success = "Full" then "Write = sent" else "Write = failed: {Error}"
```

```bash
HA_WEBHOOK="https://homeassistant.local:8123/api/webhook/your-id" jadivcode run notify.jdv
```

A webhook address works like a password, so keep it out of the program
file.

## Headers

```text
Web Header "Authorization" = Bearer {System Env "API_TOKEN"}
Web Timeout = 30
```

A header is sent with every following request.

## Receiving webhooks

```text
Import Web

Define Server = Web Server #8090
Define Hook = Web Read Hook {} on Server #8090

On Hook "/lamp"
    Write = Received: {Event}
    Write = State: {Event #"state"}
End
```

Test it from another terminal:

```bash
curl -X POST http://localhost:8090/lamp -H "Content-Type: application/json" -d '{"state": "on"}'
```

`{Event}` holds the received data. JSON becomes a value whose fields are
read with `#"name"`; anything else is plain text.

### Server properties

| Property | Meaning | Default |
|---|---|---|
| `Host` | who may connect | `127.0.0.1` (this computer only) |
| `Token` | secret the caller must send | none |
| `Reply` | text sent back to the caller | `OK` |

To accept calls from other devices, set a token as well:

```text
Set Server Host = 0.0.0.0
Set Server Token = {System Env "HOOK_TOKEN"}
```

The caller sends the token as the header `Authorization: Bearer <token>`
or as `?token=<token>` in the address. Set the properties before the first
`On Hook` line, because that line starts the server.

## All commands

| Command | Meaning |
|---|---|
| `{Web Get "url"}` | download as text |
| `{Web Json "url"}` | download and read JSON |
| `Web Post "url" = text` | send text |
| `Web Json "url" = a: 1, b: two` | send JSON |
| `Web Header "Name" = value` | add a header to every request |
| `Web Timeout = 30` | seconds to wait for an answer (default 15) |
| `{Web Status}`, `{Web Reply}` | result of the last request |
| `Define S = Web Server #8090` | a webhook server |
| `On Web Read Hook "/path" on Server #8090 "..."` | react to a webhook |
| `Start S`, `Stop S` | start, stop the server |
