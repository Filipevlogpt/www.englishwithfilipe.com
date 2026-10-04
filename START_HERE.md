# English with Filipe — Repository Repair

## Current repository status

The original repository mixes several generations of the frontend (`app.js`, `script0.js`, `script1.js`, `script2.js`, `test.js`) and references a `web/` directory that is not present on `main`.

The HTTP server in `start_server.py` expects these runtime files:
- `web/index.html`
- `web/vocab.json`
- `web/quizzes.json`
- `web/explanations.json`
- `web/trilingual.json`
- `web/assets/*`
- `web/audio/*`

Those runtime assets are missing from the current `main` tree.

## Repair branch

This branch is the cleanup target. Do not use the old script fragments as frontend entry points.

Canonical runtime structure:
- `web/index.html`
- `web/app.js`
- `web/data/vocab.json`
- `web/data/quizzes.json`
- `web/data/explanations.json`
- `web/data/trilingual.json`
- `web/assets/`
- `web/audio/`

## Data-quality warning

The supplied vocabulary data contains malformed generated example sentences in places. Some examples insert bare nouns or numbers where a verb or complete expression is required. These entries need validation before classroom use.

## Security

Never commit real teacher passwords or other secrets. The current server seeds fixed demo credentials in source code; replace this with environment variables or a first-run setup before public deployment.

## Run locally

```bash
python start_server.py
```

Then open `http://localhost:8000`.
