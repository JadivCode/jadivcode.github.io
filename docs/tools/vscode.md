# VS Code

An extension for Visual Studio Code is being prepared in the
`JadivCode/jadivcode-vscode` repository. It adds:

- syntax colors for `.jdv` files
- live checking: the findings of [the checker](checker.md) are underlined
  while you type
- quick fixes from the light bulb, and **JadivCode: Apply all fixes**
- ++f5++ to run the program in the terminal

The extension uses the `jadivcode` command, so
[install JadivCode](../install.md) first. If the command is somewhere
unusual, set its path in the `jadivcode.command` setting.

!!! note
    The extension is not published yet. Until it is, use the
    [JadivCode IDE](ide.md), which has the same checks built in.
