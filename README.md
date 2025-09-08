# Price-IQ: GPU Cloud Price Index + ROI

Daily scrapers → unified per-GPU $/hr → market baselines (median) → **Price-IQ**  
**100 = market median**; higher = cheaper. Also ships a simple ROI comparison.

### What’s in this repo
- `scrape+formula.ipynb` – scrapers, normalization, Price-IQ, ROI, backtest, finalization.
- `docs/data/latest/` – latest scrape per provider (slim schema).
- `docs/data/history/` – historical appends (for backtests).
- `docs/data/derived/` – baselines, scores, ROI, backtest JSONs for the dashboard.
- `docs/index.html` – static dashboard (GitHub Pages).

### Dashboard
Enable **Settings → Pages → Deploy from a branch → `main` /docs**  
Live at: `https://<org>.github.io/<repo>/`

### Run locally
```bash
pip install -r requirements.txt
python -m playwright install chromium
papermill "scrape+formula.ipynb" "docs/data/derived/run-output.ipynb"
python -m http.server -d docs 8000   # then open http://localhost:8000
