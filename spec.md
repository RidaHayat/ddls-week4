# KRAS pocket-residue handoff

## Decision
Tomorrow’s design team needs **five model-supported design anchors** to decide where to grow the hit series: residues whose side chains may provide contacts in the nucleotide-pocket groove, rather than blindly decorating the molecule. “Safe” means reliable local shape in the model, in the requested pocket neighbourhood, and present at the corresponding position in the assay protein. This is not a claim of experimentally proven contacts.

## Protein and model
- Owner’s assay protein: KRAS **G12D**, residues **1–169**, no tag; one protein chain.
- `data/my_construct.fasta`: the assay construct sequence, labelled G12D, residues 1–169.
- `data/KRAS_alphafold_model.cif`: a downloaded **AlphaFold Database**, non-experimental, single-chain KRAS model. The file shows database accession P01116 and residues through **189**, including the C-terminal tail; it is therefore not the assay construct and is not an exact G12D 1–169 model.
- `data/KRAS_alphafold_pae.json`: bundled confidence data with per-position reliability and a pairwise positional-uncertainty (PAE) matrix.

## Claim and residues
The exact owner claim is: provide five residues in the nucleotide-pocket neighbourhood that are suitable model-supported design anchors for growing compounds. The requested neighbourhood is approximately **10–17** (glycine-rich loop), **30–38** (switch I), and **57–67** (switch II), with nearby pocket-facing residues as needed. The shortlist must use assay numbering, retain only positions present in KRAS G12D 1–169, and keep experimental support separate: the transcript says there is compound binding/activity data but no residue-level mutagenesis or experimental structure validating these contacts.

## Matching confidence and checks
- For whether each candidate has a reliable local fold/shape, report that residue’s **per-residue pLDDT** from the mmCIF B-factor column.
- PAE is the matching confidence for claims about how separated regions/parts sit together or an interface; do not substitute a global or nearby pLDDT for that claim.
- Before using model coordinates, compare the model sequence/length and chain/assembly with the FASTA. Check the G12D mutation, the 1–169 boundary, numbering, and absence of tags. The supplied model’s canonical sequence and 189-residue tail create a construct mismatch that can break the decision, especially near the pocket; positions must be filtered to those present in the assay sequence and the mismatch must be disclosed.

## Done
Done means a concise handoff with exactly five (or an explicitly documented inability to select five) assay-compatible pocket-neighbourhood residues, each identified by assay position and identity, with its local pLDDT and the selection rationale; the model-versus-assay sequence/assembly check is reported; PAE is reported when making any parts-together claim; and the lack of residue-level experimental validation is clearly stated. No answer is structurally reported without first stating matching confidence and confirming protein identity/compatibility.
