# Repair report — repair-v7

## Confirmed structural problems in `main`

1. `start_server.py` serves from `ROOT/web`, but `main` had no `web/index.html` and no runtime JSON files. The frontend therefore could not boot as a complete site.
2. Multiple competing frontend generations existed at repository root (`app.js`, `script0.js`, `script1.js`, `script2.js`, `test.js`, plus patch scripts), making it unclear which file was canonical.
3. The frontend expected `/vocab.json`, `/quizzes.json`, `/explanations.json` and `/trilingual.json`, but those files were absent from `main`.
4. The server used fixed teacher/student demo passwords in source code.
5. The server returned `web/index.html` for missing paths, so a missing JSON asset could be returned as HTML and then fail JSON parsing in the browser.
6. The stored vocabulary source contains 978 entries, not the 2,500-entry figure claimed in older documentation.

## Fixes applied on `repair-v7`

- Added `web/index.html` as the canonical entry point.
- Added `web/styles.css`.
- Added `web/app.js` using the most complete root frontend source and changed startup to tolerate missing optional JSON.
- Added `web/vocab.json` from the uploaded vocabulary source.
- Added safe empty placeholders for the missing optional quizzes/explanations/trilingual datasets so startup no longer crashes.
- Updated `start_server.py` to use environment variables for credentials and to distinguish missing assets from SPA routes.
- Added `.gitignore` for databases, `.env` files and secret notes.
- Removed obsolete/conflicting root JavaScript/patch/database files from the repair branch.
- Updated the README and START_HERE instructions to match the actual repository.

## Vocabulary data check

- Total: 978
- A1: 221
- A2: 189
- B1: 181
- B2: 165
- C1: 222
- Duplicate English terms across the supplied source: none detected.

## Important content-quality finding

The vocabulary source itself still contains many generated/template-style examples and some grammatically unnatural examples. That is a content-quality issue, not a runtime-code issue. I did not silently rewrite those examples because the supplied source should remain traceable.

## Not yet complete

The repository still needs the real V6/V7 quiz, explanation, Romanian dictionary, audio and image assets before it can be called feature-complete.