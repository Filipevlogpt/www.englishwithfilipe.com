# English with Filipe — repaired repository

## Canonical runtime

- Browser entry point: `web/index.html`
- Frontend: `web/app.js`
- Styles: `web/styles.css`
- Vocabulary: `web/vocab.json`
- Server: `start_server.py`

Run:

```bash
python start_server.py
```

## What was fixed

- Added the missing `web/` runtime structure.
- Added a working HTML shell and stylesheet.
- Added the uploaded vocabulary bank as `web/vocab.json` (978 entries: A1 221, A2 189, B1 181, B2 165, C1 222).
- Frontend data loading is now defensive: missing optional datasets no longer crash the home page.
- Static file serving now returns 404 for missing assets instead of returning HTML for every missing JSON/asset request.
- Path traversal is blocked by the server path check.
- Removed hard-coded demo credentials from the active server code; credentials must be supplied with environment variables.
- Added `.gitignore` rules for local databases and secrets.

## Still incomplete

The current GitHub repository does not contain the complete V6 runtime bundle. The following are not yet present in this repair branch:

- full quiz dataset;
- full explanations dataset;
- full English/Portuguese/Romanian dictionary dataset;
- audio files;
- `web/assets/filipe-story.jpeg`.

The frontend uses safe empty arrays for these missing optional datasets so the site can load instead of failing at boot.
