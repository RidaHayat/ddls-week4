# Operating instructions

## Environment
- Use `uv`: create the environment with `uv venv` and run all Python with `uv run ...`. This is the cross-platform workflow.
- The handover data is in `data/`. Outputs belong in `results/`.
- Structure: `data/KRAS_alphafold_model.cif` is an AlphaFold Database mmCIF. Load its single chain and read per-residue pLDDT from the mmCIF atom-site B-factor (`_atom_site.B_iso_or_equiv`; repeated atom values represent the residue confidence). `data/KRAS_alphafold_pae.json` contains the per-position reliability and pairwise positional-uncertainty/PAE matrix. The assay sequence is `data/my_construct.fasta`.

## Version control
This folder is a git repository. Add `.env`, `.venv/`, `__pycache__/`, and `*.pyc` to `.gitignore`; never commit secrets. Commit the current state before any big change, and commit again whenever something starts working, using short, clear messages.

## Course fold service
To fold a protein sequence that is not in the AlphaFold DB, read and follow https://ddls-structure-api-8a7d6803.svc.hypha.aicell.io/skill.md. Take the fold key from the `DDLS_FOLD_KEY` variable in `.env`; load it with `set -a; source .env; set +a`, then send it as the Bearer token. Never write the key itself into `AGENTS.md` or any other committed file.

## Structural-answer rule
Never report an answer about a structure without first reporting the confidence that matches the claim, and confirming that the model is actually this protein. Use per-residue pLDDT for a fold or local region; use PAE/interface confidence for how parts sit together. Explicitly distinguish model-supported design confidence from experimental support.
