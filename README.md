# Castilleja Phylogenomics Pipeline (2025)

This repository contains scripts and workflows used for phylogenomic analyses of *Castilleja* using target enrichment (Angiosperm353) data.

## Workflow Overview

1. Raw read trimming - Trimmomatic
2. Sequence assembly and target recovery - HybPiper
3. Resolution of paralogs - ParaGone
4. Sequence alignment - Mafft
6. Sequence filtering - filtering script
7. Phylogenetic tree reconstruction - IQ-tree2, ASTRAL

---

## 1. Raw Read Trimming

**Script:**

Raw sequencing reads were cleaned using Trimmomatic to remove adapter contamination and low-quality or short reads (Bolger et al. 2014).

---

## 2. Sequence Assembly and Target Recovery

**Script:** 

Cleaned reads were mapped to the Angiosperm353 target loci using HybPiper v2.3.2 (Johnson et al. 2016).

To maximize sequence recovery, a Rubiaceae-specific target file was generated using NewTargets (McLay et al. 2021). Read mapping was performed using the Burrows–Wheeler Aligner (BWA; Li and Durbin 2009) within the HybPiper2 workflow.

Gene assembly and recovery included:

- Reference-guided assembly of target loci
- Exon alignment and scaffolding using `exonerate`
- Recovery of intronic regions using `run_intronerate`
- Recovery of paralogs
- Extraction of exon and supercontig sequences using `retrieve_sequences`

---

## 4. Resolution of paralogs

**Script:** 


---

## 5. Sequence Alignment & Filtering

**Script:** 

Recovered supercontig sequences were aligned using MAFFT (Katoh et al. 2002). To evaluate the effects of missing data, a custom Python script was used to generate datasets with varying completeness thresholds.

Filtering was performed in two steps:

1. Remove samples present in less than 30%, 50%, or 70% of loci.
2. Remove loci present in less than 30%, 50%, or 70% of samples.

Filtered alignments were subsequently cleaned using Phyutility (Smith and Dunn 2008) to remove sites with more than 50% missing data (`clean -0.5`).

This produced the final datasets used for phylogenetic analyses.

---

## 6. Phylogenetic Tree Reconstruction

**Scripts:** 

Phylogenetic relationships were inferred using both concatenation and coalescent-based approaches.

### Gene Trees

Individual gene trees were estimated using IQ-TREE 2.

### Concatenated Analyses

Concatenated phylogenetic hypotheses were reconstructed using IQ-TREE 2.

### Species Tree Estimation

Species trees were inferred from gene trees using ASTRAL-III.


## 7. Phyparts

**Scripts:** 

---


## 8. Coalesccent Simulations

**Scripts:** 

---

## 9. Divergence Dating Analysis (BEAST2)

**Scripts:** 


---
## References

- Bankevich, A. et al. 2012.
- Bolger, A.M. et al. 2014.
- Johnson, M.G. et al. 2016.
- Katoh, K. et al. 2002.
- Li, H. and Durbin, R. 2009.
- McLay, T.G.B. et al. 2021.
- Smith, S.A. and Dunn, C.W. 2008.

