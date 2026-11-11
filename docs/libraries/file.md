# File

Read and write text files.

```text
Import File
```

```text
File Write "notes.txt" = First line
File Append "notes.txt" = Second line

Write = {File Read "notes.txt"}

For each Line in {File Lines "notes.txt"}
    Write = > {Line}
End
```

| Command | Meaning |
|---|---|
| `{File Read "name"}` | the whole file as text |
| `{File Lines "name"}` | the file as a list of lines |
| `{File Exists "name"}` | `ON` when the file exists |
| `File Write "name" = text` | replace the file with the text |
| `File Append "name" = text` | add a line at the end |
| `File Delete "name"` | delete the file |

File names are relative to the folder where you started the program.
`~` means your home folder: `"~/notes.txt"`.

!!! warning
    `File Write` replaces the whole file and `File Delete` removes it
    without asking. When the file name comes from a user or from the
    network, check it first. See [writing safe programs](../security.md).
