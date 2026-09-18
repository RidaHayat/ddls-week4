For the KRAS G12D 1–169 assay construct, the five model-supported design anchors are Gly10, Val14, Gly15, Lys16, and Ser17. Their construct-matched pLDDT values range from 87.06 to 90.79. These residues can be used as structural anchors for design discussion, but the analysis does not establish experimentally validated compound contacts.

# 1. The question

Dr Yuki Tanaka needs five model-supported residues in the nucleotide-pocket neighbourhood to use as design anchors when deciding where to grow the KRAS inhibitor series for the KRAS G12D 1–169 assay construct. The answer is intended to guide design prioritisation, not to assign experimentally proven compound contacts.

# 2. The protein & the files

The assay protein is KRAS G12D, residues 1–169, represented as a single-chain monomer with no tag. The owner’s sequence is in `data/my_construct.fasta`.

The downloaded AlphaFold Database reference is `data/KRAS_alphafold_model.cif`. It is canonical KRAS P01116, residues 1–189, in a single chain. The existing AlphaFold/reference PAE file is `data/KRAS_alphafold_pae.json`. The sequence-matched fold of the assay construct is `data/KRAS_G12D_construct_1-169.pdb`.

Both structural models are predictions, not experimental structures. There is no experimental structure or residue-level mutagenesis evidence validating specific compound contacts.

# 3. The right confidence, stated plainly

The claim concerns local structural reliability in a pocket region, so the relevant measure is per-residue pLDDT. PAE is not a substitute for local pLDDT.

In the sequence-matched G12D 1–169 fold, the requested regions have the following confidence:

| Assay region | Minimum pLDDT | Mean pLDDT |
|---|---:|---:|
| 10–17 | 80.13 | 86.94 |
| 30–38 | 62.00 | 68.27 |
| 57–67 | 45.12 | 60.30 |

The selected residues are in region 10–17:

| Residue | pLDDT in G12D 1–169 fold |
|---|---:|
| Gly10 | 87.70 |
| Val14 | 89.92 |
| Gly15 | 90.79 |
| Lys16 | 87.06 |
| Ser17 | 87.03 |

The actual construct fold has an overall mean pLDDT of 85.45 and a pTM of 0.9034. The pTM is global fold information; it does not replace the local values above. The full-sequence viewer track shows pLDDT across residues 1–169 and highlights the five selected residues.

Region 10–17 is the only requested region with consistently higher pLDDT in the sequence-matched construct fold; regions 30–38 and 57–67 have substantially lower values. The lower pLDDT values in regions 30–38 and 57–67 do not by themselves establish that those regions are disordered.

# 4. The structure check

The owner’s construct is KRAS G12D, residues 1–169. The sequence-matched fold is also G12D 1–169, with one chain A, a monomeric assembly, and no residues beyond 169. Position 12 is D in the assay construct.

The AlphaFold Database reference is different: it has canonical G12 rather than D12 and contains residues 170–189, which are absent from the assay construct. The downloaded AlphaFold model is therefore useful as reference geometry but is not the exact assay construct. It is also a predicted structure, not an experimentally validated model.

# 5. The trap and the honest truth

The biggest trap is treating the canonical AlphaFold Database KRAS model as if it were the owner’s G12D 1–169 assay protein. The owner FASTA was compared with the AlphaFold model sequence, identifying the G12-versus-D12 difference and the additional 170–189 tail. The existing sequence-matched G12D fold was then used for the final residue-level confidence assessment.

A second limitation is that no residue-level mutagenesis or experimental structure demonstrates that any of the five residues makes a compound contact. Model confidence supports local structural reliability; it does not establish experimental ligand contacts or binding effects.

# 6. The answer / recommendation

Five model-supported design anchors for the KRAS G12D 1–169 construct are:

- **Gly10** — pLDDT 87.70
- **Val14** — pLDDT 89.92
- **Gly15** — pLDDT 90.79
- **Lys16** — pLDDT 87.06
- **Ser17** — pLDDT 87.03

All five are from residues 10–17 because that region has the strongest and most consistent support in the construct-matched fold. In this report, a model-supported design anchor is a residue suitable for design discussion because its local structure is relatively well supported in the model and it lies in the requested nucleotide-pocket neighbourhood. Here, 'model-supported' means supported by the predicted local structure and its pLDDT in the sequence-matched construct; it does not mean experimentally validated as safe or as a compound-contact residue.

These residues should not be presented as experimentally validated compound-contact residues. They are model-supported structural anchors for hypothesis generation and design prioritisation; the analysis does not establish that any particular one definitely contacts the inhibitor.

# 7. Caveats & next steps

The model provides predicted structural and confidence evidence, but it does not establish the ligand-bound conformation or residue-level compound contacts.

Practical next steps are to obtain or generate a structure or complex for the actual G12D 1–169 construct; use an appropriate complex prediction and interface-confidence assessment if making a binding or interface claim; and experimentally test proposed contacts with residue-level mutagenesis or structural/biophysical validation, if available.

The viewer’s PAE panel is the existing AlphaFold/reference 189×189 pairwise positional-uncertainty matrix in `data/KRAS_alphafold_pae.json`. It is not a G12D 1–169 PAE matrix. Because this analysis concerns a single-chain monomer, it makes no inter-chain interface claim.

# 8. AI-use disclosure

Agent A was used to interview the owner and clarify the biological question, construct, requested pocket regions, and decision context.

Pi/AI assistance was used to inspect the provided structure, FASTA, and confidence files; perform the computational analysis; generate the viewer; and draft and organise this report. The analyst/user verified the sequence and construct comparison, residue numbering, pLDDT values, selected residues, structure and assembly state, PAE interpretation, and final viewer panels.

AI-generated suggestions were not treated as experimental evidence. The interview transcript and Pi analysis transcript are attached as part of the submission.
