# AGENTS.md — CineMatch Project Guidelines

## Tech Stack & Architecture
- **Backend:** Python 3.11+ with **FastAPI** (`app/main.py`).
- **Data Layer:** Read from `data/movies.json` (4,825 movies). Never overwrite `data/movies.json` destructively; save cleaned/deduplicated records to `data/movies_clean.json` or load them in-memory on startup.
- **Algorithms:** Pure Python + standard library (`math`, `collections`, `re`, `unicodedata`) or `scikit-learn`/`numpy` if installed. Avoid heavy external ML dependencies or external API calls—everything must run 100% offline.
- **Frontend:** Server-rendered HTML (`app/templates/index.html`) using **Tailwind CSS (via CDN)** and **HTMX** or vanilla Fetch JS. Do NOT scaffold a separate Node/React/Vite build pipeline.

## Engineering & Verification Rules
1. **Inspect Before Coding:** Always inspect the actual schema and edge cases of `data/movies.json` before writing data-cleaning or recommendation logic.
2. **Test-Driven Verification:** Every data cleaning module (`app/deduplicate.py`) and recommendation algorithm (`app/recommender.py`) MUST have corresponding unit tests in `tests/` run via `pytest`.
3. **Side-by-Side Algorithm Comparison:** Keep both the `naive` (v1) and `smart` (v2) recommendation modes accessible via API query parameters (`?mode=naive` vs `?mode=smart`) so users can visually compare algorithm quality in the UI.
