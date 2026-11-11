# Install

JadivCode runs on Linux (including Raspberry Pi OS) and needs Python 3.9
or newer, which almost every Linux system already has.

## Install or update

```bash
curl -fsSL https://raw.githubusercontent.com/JadivCode/jadivcode/main/install.sh | bash
```

The installer puts everything in your home folder
(`~/.local/share/jadivcode` and `~/.local/bin/jadivcode`). It never uses
`sudo`. Run the same command again to update.

Check that it works:

```bash
jadivcode --version
```

!!! note "Command not found?"
    Add `~/.local/bin` to your `PATH` and open a new terminal:

    ```bash
    echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
    ```
You can optionally use the graphical IDE (recommended)

```bash
curl -fsSL https://raw.githubusercontent.com/JadivCode/jadivcode-ide/main/install.sh | bash
```

## Optional parts

Install these only when you need them.

| For | Command |
|---|---|
| GUI windows | `sudo apt install python3-tk` |
| Real Raspberry Pi pins | `sudo apt install python3-gpiozero python3-lgpio` |
| The AI helper | `python3 -m pip install --user anthropic` |

Without the GPIO packages, pins are simulated. Without Tk, windows are
simulated. Your programs still run.

## Uninstall

```bash
curl -fsSL https://raw.githubusercontent.com/JadivCode/jadivcode/main/install.sh | bash -s -- --uninstall
```
