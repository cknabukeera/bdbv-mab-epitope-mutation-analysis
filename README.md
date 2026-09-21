# bdbv-mab-epitope-mutation-analysis

Genomic and structural analysis of monoclonal antibody (mAb) epitopes on the Bundibugyo virus (BDBV) glycoprotein (GP), to assess the predicted efficacy of Ebola virus (EBOV) mAbs against the 2026 Bundibugyo virus disease (BVD) outbreak in the Democratic Republic of the Congo and Uganda. Therefore, we aimed to answer two questions; how different is Zaire from  our BDBV, and could existing Zaire mAbs neutralize it?

**Published paper:**

**Preprint Paper:** *Early insights into predicted efficacy of Ebola monoclonal antibodies for the 2026 Bundibugyo virus disease outbreak*
Preprint: DOI:https://doi.org/10.21203/rs.3.rs-10270397/v1

---

## Overview

Two mAb treatments are approved for Ebola virus disease: mAb114 (Ebanga) and the three-antibody cocktail Inmazeb (atoltivimab, odesivimab, maftivimab). The experimental pan-ebolavirus cocktail MBP134 (ADI-15878 and ADI-15946) targets highly conserved epitopes. Their efficacy against BDBV is uncertain.

This repository contains the code, data references and results for an in silico assessment based on:

- 44 BDBV whole-genome sequences from Uganda and DRC (2007, 2012 and 2026 outbreaks, including 12 from the 2026 outbreak, retrieved 25 May 2026),
- To crosscheck the validity of mutations observed above across the outbreak,
- Further 462 sequences of the 2026 BDBV outbreak from Pathoplexus (as of Aug 13, 2026) were assessed for presence and preservation of these mutations across the 2026 BDBV outbreak genomes.
- Mapping of mAb epitopes from EBOV GP onto BDBV GP,
- AlphaFold 3 modelling of GP-antibody complexes,
- Rosetta in silico mutagenesis and binding-energy calculations,
- Glycosylation modelling at Asn563.

## Data used
### Genome sequences

The 44 BDBV whole-genome sequences used in this study were obtained from
[Pathoplexus](https://pathoplexus.org). Accession numbers are listed in
[`data/pathoplexus_accessions.txt`](data/pathoplexus_accessions.txt) and below.

<details>
<summary>Pathoplexus accessions (n = 44)</summary>

| # | Accession | # | Accession | # | Accession | # | Accession |
|---|-----------|----|-----------|----|-----------|----|-----------|
| 1 | CL023421 | 12 | PP_006Y8R6.1 | 23 | PP_006X6NG.1 | 34 | PP_006X62P.1 |
| 2 | CL0023559 | 13 | PP_006Y8S4.1 | 24 | PP_006X6PE.1 | 35 | PP_006X5YX.1 |
| 3 | CL0023560 | 14 | PP_006X5ZV.1 | 25 | PP_006X6QC.1 | 36 | PP_006X5RB.1 |
| 4 | PP_006XCJJ.1 | 15 | PP_006X6EZ.1 | 26 | PP_006X6RA.1 | 37 | PP_006X6A7.1 |
| 5 | PP_006XHKB.2 | 16 | PP_006X6FX.1 | 27 | PP_006X6S8.1 | 38 | PP_006X6C3.1 |
| 6 | PP_006XHL9.2 | 17 | PP_006X6GV.1 | 28 | PP_006X6T6.1 | 39 | PP_006X6D1.1 |
| 7 | PP_006XXY5.1 | 18 | PP_006X6HS.1 | 29 | PP_006X6V2.1 | 40 | PP_006X6ZU.1 |
| 8 | PP_006Y8NC.2 | 19 | PP_006X6JQ.1 | 30 | PP_006X6W0.1 | 41 | PP_006X63M.1 |
| 9 | PP_006Y8PA.2 | 20 | PP_006X6KN.1 | 31 | PP_006X6XY.1 | 42 | PP_006X64K.1 |
| 10 | PP_006Y8Q8.2 | 21 | PP_006X6LL.1 | 32 | PP_006X6YW.1 | 43 | PP_006X68B.1 |
| 11 | PP_006Y8R6.1* | 22 | PP_006X6MJ.1 | 33 | PP_006X60T.1 | 44 | PP_006X699.1 |

</details>

### Reference sequences and Protein structures
| Data | Source | Notes |
|------|--------|-------|
| EBOV GP reference | NP_066246.1 | NC_002549.1|
| BDBV GP reference (2007) | YP_003815435.1 |NC_014373.1|
| Experimental structures | PDB: 5FHC (EBOV GP-mAb114), 7TN9 (EBOV GP-Inmazeb), 6EA7 and 6MAM (EBOV GP with ADI-15878 / ADI-15946), 6DZM (BDBV GP-ADI-15878) | |

## Key findings

- MBP134 epitopes are conserved across all analysed BDBV sequences, and both components are predicted to bind BDBV GP at their designated sites.
- The mAb114 epitope carries the substitutions E112D and P116A, and mAb114 is predicted to bind BDBV GP off-target.
- In Inmazeb, odesivimab is predicted to bind its epitope alone, while atoltivimab and maftivimab are not. The complete trimeric cocktail is predicted to bind BDBV GP at the target epitopes.
- Two GP substitutions were unique to the 2026 outbreak sequences: Y387H and R506S.
- These amino acid substitutions observed in the BDBV epitopes remained consistent across a wider number of sequences from the outbreak (n=494) accessed and analysed from the Pathoplexus database as of Aug, 13th - 2026.

## Methods (summary)

1. **Sequence retrieval and QC:** Pathoplexus and CPHL sequences; Nextclade quality control; GP sequences extracted.
2. **Alignment and mutation analysis:** EMBOSS pairwise alignment (EBOV vs BDBV GP); Clustal Omega in Geneious Prime; mutation calling in Nextclade; functional impact with SIFT4G.
3. **Epitope mapping:** EBOV GP epitopes mapped onto the alignment of 44 BDBV GP sequences.
4. **Structure prediction:** AlphaFold 3 for BDBV and EBOV GP with mAb114, individual Inmazeb components, the Inmazeb trimeric cocktail, and MBP134 components; visualization in ChimeraX; comparison with experimental structures.
5. **In silico mutagenesis:** BDBV epitope mutations introduced into EBOV GP-antibody complexes; structures relaxed with Rosetta FastRelax; binding-energy changes (ΔΔG) with Rosetta ddG.
6. **Glycosylation modelling:** Man5GlcNAc2 glycan added at Asn563 with PyRosetta (SimpleGlycosylateMover, GlycanTreeModeler); interface analysis with InterfaceAnalyzerMover.

Computations were run on the HPC infrastructure at ACE-Uganda, Makerere University.

## Repo Structure
- Each mAbs and their BDBV epitope mutations, energy calculations
- The AF3 predicted Structures are in the Structures folder
- The Results folder has the results of the energy calculations

## Requirements

- Python and PyRosetta, Rosetta (FastRelax, ddG)
- AlphaFold 3 
- Nextclade, SIFT4G, EMBOSS, Clustal Omega
- UCSF ChimeraX and PyMOL for visualization
- Geneious Prime v2026.1.1 (commercial; used for alignment and annotation)

## Citation

If you use this repository, please cite:

```
Nabukeera KC, Luakanda-Ndelemo G, Semawule S, et al. (2026). Early insights into viability of
Ebola monoclonal antibodies for the 2026 Bundibugyo virus disease outbreak.DOI: 10.21203/rs.3.rs-10270397/v1
```

## Authors and contact

Full author list in the paper.

**First author:** Kevin Cissy Nabukeera, [kc.nabukeera@gmail.com] | ORCID: https://orcid.org/0009-0009-8319-1853

**Corresponding author:** Dr. Daudi Jjingo, [djjingo@idi.co.ug]
