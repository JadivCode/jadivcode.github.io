# jadivcode.github.io

Source of the JadivCode documentation at <https://jadivcode.github.io>.

The site is built with [MkDocs](https://www.mkdocs.org/) and the Material
theme. Pages are Markdown files in `docs/`.

## Preview locally

```bash
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt
.venv/bin/mkdocs serve
```

## Publishing

Every push to `main` builds the site and deploys it with GitHub Actions.
In the repository settings, **Pages → Source** must be set to
**GitHub Actions**.

## License

MIT License. See [LICENSE](LICENSE).
