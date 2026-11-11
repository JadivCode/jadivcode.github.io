# JadivCode IDE

A desktop editor made for JadivCode. You can type programs, build them
from blocks, or design windows and web pages with the mouse.

![The JadivCode IDE](../assets/ide.png)

## Install

Install [JadivCode](../install.md) first, then:

```bash
curl -fsSL https://raw.githubusercontent.com/JadivCode/jadivcode-ide/main/install.sh | bash
```

```bash
sudo apt install python3-pyqt5
```

Start it from the application menu or with `jadivcode-ide`.

## The window

| Part | What it does |
|---|---|
| Editor | Colors the words, numbers the lines, indents blocks for you |
| Problems | Lists mistakes and unsafe code while you type |
| Output | Shows what the program writes; type answers for `Ask` in the line below |
| Help | The whole language and every library, with a search box |

## Running

| Button | Key | Meaning |
|---|---|---|
| Run | ++f5++ | Save and run the program |
| Run simulated | ++shift+f5++ | Run without hardware or a screen |
| Stop | ++ctrl+f5++ | Stop the running program |

## Fixing problems

A problem is underlined in the editor and gets a dot next to its line
number: red for an error, yellow for a warning, blue for a tip. Select it
in **Problems** to read the hint.

- **Apply fix** repairs the selected problem when a fix is available.
- **Fix all** (++ctrl+shift+f++) applies every available fix.
- ++ctrl+z++ undoes a fix.

## Help panel

Type a word such as `button`, `loop` or `wait` into the search box.
Select an entry to read what it does and see an example. Double-click it,
or press **Insert into program**, to put the example into your program.

The panel contains every statement, every helper, every command of every
library and every finding of the checker.

## Blocks

**Tools → Blocks** (++ctrl+b++) builds a program without typing.

![The block editor](../assets/blocks.png)

1. Add blocks from the list on the left.
2. Drag from a coloured dot at the bottom of a block to the block that
   comes next.
3. Select a block to fill in its values on the right.
4. Press **Make the program**.

| Block | Meaning |
|---|---|
| When the program starts | The beginning of the main program |
| When this is used | Runs its blocks when an item, pin or event is used |
| Write, Ask, Define, Set, Wait | The statements of the same name |
| If | Three dots: `yes`, `no`, and `next` for what happens afterwards |
| Repeat, While, Forever | An `inside` dot for the blocks they repeat |
| Any line | One line of JadivCode, for everything else |
| Stop the program | Ends the program |

Drag a dot to empty space to remove its link. Press ++delete++ to remove
the selected block.

The blocks are saved in the last line of the program (`// blocks: ...`).
Open **Blocks** again to continue. Text you change by hand is not read
back into the blocks.

## Designers

**Tools → Window designer** (++ctrl+d++) and **Web page designer**
(++ctrl+shift+d++) let you place items with the mouse.

![The window designer](../assets/designer.png)

1. Add texts, buttons, inputs, checkboxes and sliders from the left.
2. Drag them into place. They snap to a 5 pixel grid.
3. Edit the name, text and size on the right.
4. Press **Insert code**.

The designer writes lines such as:

```text
Define Button1 = GUI Button "Press me" at 20, 60 size 110, 32
```

and, when you leave the box ticked, an `On Button1 ... End` block for each
button. It reads items that are already in the program, so you can reopen
a design later.

A web page places items from top to bottom in the order you arrange them.

## AI helper

**Tools → Ask AI** explains the problems in plain words. It is optional
and asks before it sends your program anywhere. See [AI helper](ai.md).
