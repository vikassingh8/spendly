# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

"Spendly" — a Flask expense tracker built as a step-by-step teaching project. The app is a scaffold: only the static pages work; everything else is a placeholder to be implemented in numbered steps.

## Layout note

The git repo root (`expense-tracker/`) contains a nested `expense-tracker/` directory, which is the actual app. Run all commands from the inner directory (where `app.py` lives). `venv/` and `__MACOSX/` at the outer level are git-ignored.

## Commands

```
pip install -r requirements.txt   # flask, werkzeug, pytest, pytest-flask
python app.py                     # dev server at http://localhost:5001 (debug=True)
pytest                            # run tests (none exist yet)
pytest path/to/test_file.py::test_name   # run a single test
```

On Windows the venv is activated with `..\venv\Scripts\activate`.

## Architecture

- `app.py` — single Flask app with all routes defined inline. Implemented routes (`/`, `/register`, `/login`, `/terms`, `/privacy`) just render templates; there are no POST handlers, forms are not wired up, and no sessions/auth exist yet.
- Placeholder routes (`/logout`, `/profile`, `/expenses/add`, `/expenses/<id>/edit`, `/expenses/<id>/delete`) return stub strings labelled with the step that should implement them (Steps 3, 4, 7, 8, 9). Keep those step labels/URLs when replacing stubs.
- `database/db.py` — empty stub with comments specifying the intended API: `get_db()` (SQLite connection with `row_factory` and foreign keys enabled), `init_db()` (`CREATE TABLE IF NOT EXISTS`), `seed_db()` (sample dev data). This is Step 1.
- `templates/` — all pages extend `base.html` (navbar, footer, blocks `title`, `head`, `content`). Use `url_for(...)` for links and static assets.
- `static/css/style.css`, `static/js/main.js` — single shared stylesheet and script; fonts (DM Serif Display, DM Sans) are loaded from Google Fonts in `base.html`.
