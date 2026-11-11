# Time

The current date and time.

```text
Import Time
```

```text
Write = It is {Time Now} on {Time Weekday}
If {Time Hour} >= 22 then Write = Time to sleep
```

| Command | Example result |
|---|---|
| `{Time Now}` | `14:05:09` |
| `{Time Date}` | `2026-11-11` |
| `{Time Hour}`, `{Time Minute}`, `{Time Second}` | `14`, `5`, `9` |
| `{Time Day}`, `{Time Month}`, `{Time Year}` | `11`, `11`, `2026` |
| `{Time Weekday}` | `Wednesday` |
| `{Time Stamp}` | seconds since 1970, for measuring durations |
| `{Time Format "%d.%m.%Y %H:%M"}` | `11.11.2026 14:05` |

## Measuring how long something takes

```text
Define Began = {Time Stamp}
Wait 2s
Write = That took {Round((Time Stamp) - Began, 1)} seconds
```

To pause a program use `Wait`, which needs no library: `Wait 5s`.
