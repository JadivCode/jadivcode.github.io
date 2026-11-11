# AI helper

The built-in [checker](checker.md) works offline and is always on. On top
of it, JadivCode can ask an AI model (Claude, made by Anthropic) to explain
the problems in plain words and show a corrected program.

The AI helper is **optional and off by default**. Nothing is sent anywhere
unless you run it.

## Set up

1. Install the package:

    ```bash
    python3 -m pip install --user anthropic
    ```

2. Create an API key at <https://platform.claude.com> and put it in your
   environment:

    ```bash
    export ANTHROPIC_API_KEY="your-key"
    ```

   Add that line to `~/.bashrc` to keep it. Do not put the key in a `.jdv`
   file.

## Use

```bash
jadivcode explain program.jdv
jadivcode explain program.jdv Why does the lamp never switch off?
```

## Good to know

- **Privacy:** the whole program file and the checker findings are sent to
  the Claude API. Remove secrets from the file first.
- **Cost:** requests are billed to your own Anthropic account.
- **Check the answer:** the AI can be wrong. Run `jadivcode check` on the
  corrected program before you trust it.
- Choose another model with the `JADIVCODE_AI_MODEL` environment variable.
