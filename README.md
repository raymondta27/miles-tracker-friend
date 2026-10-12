# Miles Tracker

A single-file web app (works offline, installs to your phone's home screen) that tells you which credit card to use for each purchase, tracks bonus caps, and shows where your money goes.

Set up for these five cards: **UOB Lady's Card, DBS Woman's World Mastercard, HSBC TravelOne, UOB PRVI Miles, Citi Cash Back+**. Citi Cash Back+ pays cash back, not miles. The app compares it with the miles cards at a value per mile you choose (default 1.5 cents, under More → Backup & settings).

- App: `index.html` (built from `src/` with `cd src && python3 build.py`)
- Your data stays in your browser. You can also sync it to **your own private** GitHub repo (More → Sync), and export JSON (backup) or CSV (reports) any time.
- Setup and handover guide: [HANDOVER.md](HANDOVER.md)
- Optional command-line tool: [tools/README.md](tools/README.md)

Tests: `node src/test-friend-engine.js && node src/test-sync.js && node src/test-budget.js && node tools/test-cli.js` (UI smoke test: `src/ui-smoke.js`, needs puppeteer-core + Chrome).

Card rules were checked 12 Oct 2026 against bank pages and T&Cs (links are in the app under Cards → Details). Banks change rules often, so check before you rely on them.
