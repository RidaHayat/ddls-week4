# KRAS G12D Step 5 Core

Small FastAPI/Tailwind presentation of the completed Step 5 structure analysis. It reads the supplied AlphaFold DB mmCIF from `data/` and presents the already-completed confidence values; it does not rerun analysis.

## Run

```bash
uv run uvicorn app:app --reload --port 8000
```

Open <http://127.0.0.1:8000/>.
