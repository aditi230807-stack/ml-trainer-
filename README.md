# ML Trainer: Train & Test with Your Own CSV

FastAPI + scikit-learn app. Upload any CSV, pick a target and features, train a
regression or classification model, then predict from a sample row or manual input.

## Run locally
```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```
Open http://127.0.0.1:8000 (API docs at /docs).

## API
| Method | Path | Purpose |
|---|---|---|
| GET | `/api/dataset` | current dataset, columns, preview |
| POST | `/api/upload` | upload a CSV |
| POST | `/api/train` | train (`problem_type`, `model_type`, `target`, `features`) |
| POST | `/api/predict-sample` | predict a random held-out row |
| POST | `/api/predict-manual` | predict from typed values |

## Deploy (Render, free)
1. Push this folder to GitHub.
2. render.com -> New -> Web Service -> pick the repo.
3. Build: `pip install -r requirements.txt`
   Start: `uvicorn main:app --host 0.0.0.0 --port $PORT`
   (or use the included `render.yaml` via New -> Blueprint)
4. Deploy. Your public URL appears at the top of the service page.
