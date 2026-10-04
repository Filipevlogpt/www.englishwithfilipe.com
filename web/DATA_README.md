# Runtime data

The current repository snapshot contains a validated vocabulary source, but the complete V6 runtime data bundle is not present on the main branch.

This repair branch adds `web/vocab.json` from the uploaded vocabulary source and uses empty arrays for the missing optional datasets so the site no longer crashes at startup.

Populate these files before treating the platform as feature-complete:
- `web/quizzes.json`
- `web/explanations.json`
- `web/trilingual.json`
- `web/audio/*`
- `web/assets/filipe-story.jpeg`

The frontend is defensive: missing optional JSON no longer prevents the home page and vocabulary library from loading.