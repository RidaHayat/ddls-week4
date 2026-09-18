# DDLS 2026 — Week 4 interview transcript

**Lab:** Interview a Structural-Biology Data Owner
**Data owner:** Dr. Yuki Tanaka — Medicinal chemist / drug-discovery researcher
**Student:** Rida Hayat <rida.hayat@studenti.univr.it>
**Exported:** 2026-09-17T22:12:57+00:00

> This is the record of your interview with the data owner. Hand it to your analyst agent as the raw source for `AGENTS.md` and `spec.md`.

---

**You**:

Could you walk me through the protein you're working with, what structure/model you have, and the specific question or decision you're hoping to answer with it?

**Dr. Yuki Tanaka**:

I’m Dr Yuki Tanaka, a medicinal chemist at Uppsala, working on a KRAS inhibitor series. I have the AlphaFold KRAS structure, the sequence for the protein used in our assays, and the bundled confidence file. I want the nucleotide-pocket neighbourhood read off clearly—especially the groove around the glycine-rich loop and switch regions, and the residues my compounds can actually engage. Can you turn that into the **five safest pocket residues** for tomorrow’s design handoff?

**You**:

Thanks. When you say the “nucleotide-pocket neighbourhood,” which specific residues or residue range are you planning to rely on for the design handoff? Also, can you confirm whether the structure corresponds exactly to the KRAS sequence used in your assays, including the same length and any mutations, truncations, or tags?

**Dr. Yuki Tanaka**:

For the pocket, I mean roughly residues **10–17** (the glycine-rich loop), **30–38** (switch I), and **57–67** (switch II), with nearby pocket-facing residues as needed.

And no—the assay protein is **KRAS G12D**, trimmed to **residues 1–169**. The downloaded model is the database KRAS model with the C-terminal tail present; I had assumed it was interchangeable, but it is not an exact copy of the assay construct. The mutation matters right in the pocket neighbourhood, so use the assay numbering and sequence for the handoff.

**You**:

ust to make sure I have the basics right: which KRAS protein/construct are you working with, and what is the source of the structure you're using? Is it an experimental structure or an AlphaFold prediction? If it's an AlphaFold prediction, is it from the AlphaFold Database or one you generated yourself? Also, is the model a single chain or an assembly?

**Dr. Yuki Tanaka**:

It’s the **G12D KRAS construct used in our assays, residues 1–169**—no tag is part of the construct I’m handing over here. The structure is **not experimental**; it’s the downloaded **AlphaFold Database model**, not something I generated. It is a **single KRAS chain**, not a multi-chain assembly. Does the file show anything unexpected beyond that?

**You**:

What files are you handing over with the model—FASTA, PDB or mmCIF, and confidence files? For the structure, what confidence information is available, such as per-residue confidence or a PAE/error matrix? And does the sequence in the structure file correspond to the canonical database sequence or to the G12D 1–169 assay construct?

**Dr. Yuki Tanaka**:

The handover contains:

- `KRAS_alphafold_model.cif` — the **AlphaFold Database mmCIF model**; no PDB file.
- `my_construct.fasta` — the assay protein sequence.
- `KRAS_alphafold_pae.json` — the bundled confidence data, including per-position reliability and a pairwise positional-uncertainty matrix.

The sequence represented by the model is the database KRAS sequence with the C-terminal tail, **not the G12D 1–169 assay construct**. I know—that should have been obvious to me before I called them interchangeable. Do you want the shortlist based on the model’s confidence first, then filtered to residues present in the assay protein?

**You**:

Before I decide on the shortlist, I want to separate the structure evidence from the assay construct. What is the exact decision the design team will make from these residues tomorrow, and what would make a residue “safe” for that decision? Also, do you have any experimental evidence supporting the pocket or these specific residues, or are you relying entirely on the AlphaFold model?

**Dr. Yuki Tanaka**:

Tomorrow they’ll use the five residues to decide **where to grow the hit series**—which substituents might make contacts in the nucleotide-pocket groove, rather than simply decorating the molecule blindly. “Safe” means a residue has a reliable local shape in the model, lies in that pocket neighbourhood, and exists at the same position in the **G12D 1–169 assay protein**; a well-predicted residue elsewhere is useless.

We have compound binding and activity data, but no residue-level mutagenesis or experimental structure validating these particular contacts. So the shortlist would rely on the AlphaFold model plus KRAS pocket chemistry, not direct experimental proof. Are you separating “safe for design” from “experimentally confirmed,” or do you want only residues with both?

**You**:

Let me play that back to make sure I have it right: you need five residues for tomorrow’s KRAS G12D 1–169 design handoff, specifically residues in the nucleotide-pocket neighbourhood that have reliable local structural confidence and are actually present at the corresponding positions in the assay construct. The available AlphaFold model is the canonical KRAS model with the C-terminal tail, so it is not an exact model of your assay construct, and there is no residue-level experimental structure or mutagenesis confirming these contacts; the shortlist therefore needs to distinguish model-based design confidence from experimental confirmation.  Is that an accurate summary, or would you change anything?

**Dr. Yuki Tanaka**:

Yes, that’s accurate. The five should be **model-supported design anchors**, restricted to the folded pocket region and positions present in our G12D 1–169 assay construct—not claims of experimentally proven contacts. Keep the two labels separate: **local model confidence** versus **experimental support**, which is absent at residue level. Do you have the residue-level confidence values extracted yet, or are you asking me to define the filtering rule?
