# KRAS G12D Structural Bioinformatics: AlphaFold Confidence Profiling & Pocket Design Anchors

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![Structure](https://img.shields.io/badge/AlphaFold-Confidence%20Evaluation-emerald.svg)](https://alphafold.ebi.ac.uk/)
[![Interactive Viewer](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-brightgreen.svg)](https://ridahayat.github.io/ddls-week4/)
[![FastAPI](https://img.shields.io/badge/FastAPI-Dashboard-teal.svg)](https://fastapi.tiangolo.com/)

An end-to-end structural bioinformatics workflow evaluating local model confidence (pLDDT and PAE) in the oncogenic **KRAS G12D** mutant (residues 1–169 assay construct). This project assesses whether deep-learning structural models can reliably guide the identification of residue-level design anchors for growing small-molecule inhibitor series targeting the nucleotide-binding interface.

Developed as part of the **Data-Driven Life Sciences (DDLS)** programme (SciLifeLab & KTH Royal Institute of Technology).

---

## 🔬 Biological Motivation & Research Question

KRAS is one of the most frequently mutated oncogenes in human cancers, with the **G12D** substitution accounting for a substantial portion of pancreatic ductal adenocarcinomas, colorectal tumours, and non-small cell lung cancers. Developing targeted small-molecule inhibitors requires identifying stable pocket neighbourhoods that can accommodate chemical substituents without causing steric clashes or relying on highly flexible loop regions.

### Key Computational Questions:
1. **Model Identity & Boundary Checks:** How does the canonical AlphaFold Database reference (wild-type G12, 189 residues) compare with the experimental assay construct (G12D, 169 residues)?
2. **Local Confidence vs Global Fold:** Can global model confidence metrics (e.g., pTM) be trusted when making residue-level medicinal chemistry design choices?
3. **Design Anchor Shortlisting:** Which residues in the nucleotide-pocket neighbourhood exhibit high, consistent structural confidence (pLDDT) to serve as design anchors for series expansion?

---

## 📊 Structural Confidence Assessment

### Regional pLDDT Comparison

Local structural confidence was assessed across three candidate functional regions using the construct-matched KRAS G12D (1–169) fold:

| Pocket Region | Functional Context | Minimum pLDDT | Mean pLDDT | Structural Interpretation |
| :--- | :--- | :---: | :---: | :--- |
| **Residues 10–17** | **Phosphate-binding P-loop** | **80.13** | **86.94** | **Consistently high local confidence; rigid scaffold.** |
| **Residues 30–38** | **Effector-binding Switch I** | 62.00 | 68.27 | Moderate/low confidence; elevated conformational flexibility. |
| **Residues 57–67** | **Switch II catalytic region** | 45.12 | 60.30 | Low confidence; highly dynamic and disordered state. |

> **Global Fold Metrics:** Overall mean pLDDT = `85.45`, pTM = `0.9034`. While global pTM indicates an overall well-predicted tertiary topology, local pLDDT reveals marked regional divergence in conformational reliability.

---

## 🎯 Model-Supported Design Anchors

Five residues in the **P-loop region (10–17)** were identified as high-confidence design anchors:

| Residue | Position | Construct-Matched pLDDT | Local Structural Role |
| :---: | :---: | :---: | :--- |
| **Gly** | 10 | **87.70** | P-loop backbone entry; rigid geometric anchor |
| **Val** | 14 | **89.92** | Hydrophobic side-chain bordering nucleotide cleft |
| **Gly** | 15 | **90.79** | Highest confidence score; tight turn coordination |
| **Lys** | 16 | **87.06** | Crucial basic side-chain involved in pocket electrostatics |
| **Ser** | 17 | **87.03** | Conserved hydroxyl coordination motif |

```
P-Loop Sequence:  10 - G A G G V G K S - 17
Selected Anchors:      *       * * * *
pLDDT Scores:        87.7    89.9 90.8 87.1 87.0
```

*Note: These residues serve as structural design anchors for hypothesis generation and analogue prioritisation; computational model confidence does not substitute for empirical mutational or crystallographic binding validation.*

---

## 🌐 Interactive 3D Viewer & Presentation

An interactive 3D structural viewer built with **Reveal.js** and **3Dmol.js** allows visual inspection of:
- Residue-level pLDDT coloring mapped onto the construct structure.
- Side-by-side comparison between AlphaFold canonical reference and G12D assay construct.
- Full sequence pLDDT bar charts highlighting design anchor candidates.

👉 **[Launch Interactive 3D Viewer (GitHub Pages)](https://ridahayat.github.io/ddls-week4/)**

---

## 💻 Local Execution & Web App

### Prerequisites
- Python 3.9+
- `pip` or `uv`

### Installation
```bash
git clone https://github.com/RidaHayat/ddls-week4.git
cd ddls-week4
pip install -r requirements.txt
```

### Reproducible Analysis
To parse the structure files, extract per-residue pLDDT metrics, and generate `results/results.json`:
```bash
python analysis.py
```

### Run Local Dashboard
To launch the interactive FastAPI/Tailwind interface:
```bash
uvicorn app:app --reload --port 8000
```
Open your browser at: `http://127.0.0.1:8000/`

---

## 📂 Repository Structure

```
ddls-week4/
├── analysis.py              # Computational pipeline parsing mmCIF, PDB, and PAE JSON
├── app.py                   # FastAPI application serving interactive dashboard
├── requirements.txt         # Core dependencies (FastAPI, Uvicorn)
├── .gitattributes           # Language statistics configuration
├── data/
│   ├── my_construct.fasta   # Assay construct sequence (KRAS G12D 1–169)
│   ├── KRAS_G12D_construct_1-169.pdb # Sequence-matched predicted fold
│   ├── KRAS_alphafold_model.cif       # Canonical AlphaFold DB reference (1–189 WT)
│   └── KRAS_alphafold_pae.json        # Predicted Aligned Error (PAE) matrix
├── docs/
│   └── index.html           # Standalone interactive 3D viewer for GitHub Pages
├── results/
│   └── results.json         # Computed regional and residue-level pLDDT metrics
└── report.md                # Detailed technical and methodological report
```

---

## 📚 References & Resources

1. Jumper, J., Evans, R., Pritzel, A. et al. *Highly accurate protein structure prediction with AlphaFold.* **Nature** 596, 583–589 (2021). https://doi.org/10.1038/s41586-021-03819-2
2. Canon, J., Rex, K., Saiki, A.Y. et al. *The clinical KRAS(G12C) inhibitor AMG 510 drives anti-tumour immunity.* **Nature** 575, 217–223 (2019).
3. Data-Driven Life Sciences (DDLS) Programme, SciLifeLab & KTH Royal Institute of Technology.
