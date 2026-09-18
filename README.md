# KRAS G12D Step 5 Core

Small FastAPI/Tailwind presentation of the completed Step 5 structure analysis. It reads the supplied AlphaFold DB mmCIF from `data/` and presents the already-completed confidence values; it does not rerun analysis.

## Run

```bash
uv run uvicorn app:app --reload --port 8000
```

Open <http://127.0.0.1:8000/>.

## Reproducible results

Run `uv run python analysis.py` to parse the owner FASTA, AlphaFold mmCIF, construct-matched PDB, and reference PAE JSON. The script writes `results/results.json` and copies the required structure/PAE inputs into `results/`. `app.py` reads those disk-backed results and files; no database is used.
