# m6A RNA Modification Landscape in Triple-Negative Breast Cancer
## Epitranscriptomic Analysis | MDA-231 | 92 Cancer Genes | Oxford Nanopore Direct RNA Sequencing

**Author:** Somrita Ghosh  
**Affiliation:** MSc Molecular Biology and Biotechnology, Queen's University Belfast (2024)  
**Institute:** Patrick G Johnston Centre for Cancer Research / Institute for Global Food Security  

---

## Overview

This repository contains the second of two complementary epitranscriptomic 
analyses from my MSc research at Queen's University Belfast. While 
[Project 1](https://github.com/somritaghosh-1/polya-tnbc-nanopore) 
characterised polyA tail length regulation across 96 cancer genes in MDA-231 
triple-negative breast cancer cells, this project maps the N6-methyladenosine 
(m6A) RNA modification landscape across the same gene set — identifying where 
m6A sites cluster across transcript regions and what this means for 
post-transcriptional regulation in TNBC.

Together, these two datasets represent the first combined polyA tail length and 
m6A modification profile of a clinically validated cancer gene panel in 
triple-negative breast cancer, generated from a single Oxford Nanopore direct 
RNA sequencing experiment.

---

## Key Findings

- **9,826 m6A modification sites** detected across **92 cancer-associated genes** 
  in MDA-231 TNBC cells using Oxford Nanopore direct RNA sequencing with 
  Dorado modification-aware basecalling
- **Strong 3'UTR enrichment:** 72.7% of all m6A sites (7,148) localise to the 
  3'UTR, consistent with m6A-mediated mRNA decay via YTHDF2 recruitment — 
  the dominant mechanism of m6A-regulated transcript turnover
- **24.6% of sites in the CDS** (2,420 sites) suggest additional roles in 
  translation elongation speed and ribosome pausing across these cancer transcripts
- **Top m6A-modified genes:** THBS1 (418 sites), ITGA3 (396), TIMP3 (345), 
  ABL1 (299), BCL2L1 (289) — all cancer-relevant genes with roles in invasion, 
  apoptosis resistance, and oncogenic signalling
- **Integrin family spotlight:** All detected integrin subunits carry both 
  above-average polyA tails (from Project 1) and significant m6A modification 
  burden — suggesting multi-layered post-transcriptional regulation sustains 
  constitutive integrin expression in MDA-231 invasiveness
- **m6A burden does not predict polyA tail length:** Pearson r = 0.109 
  (p = 0.372) for total m6A count vs mean polyA length across 60 shared genes — 
  indicating that m6A site density alone does not determine transcript stability, 
  and that the two regulatory layers operate with substantial independence. 
  This is biologically interpretable: m6A effects on stability depend on which 
  reader proteins are expressed, not just site count.

---

## Figures

![Metagene Distribution](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig1_Metagene_Distribution.png)

![m6A Sites Per Gene](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig2_Sites_Per_Gene.png)

![Regional Breakdown by Functional Group](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig3_Regional_By_Group.png)

![m6A vs PolyA Correlation](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig4_m6A_vs_PolyA_Correlation.png)

![Integrin Combined Profile](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig5_Integrin_Combined.png)

---

## Repository Structure
```
m6a-epitranscriptomics-tnbc/
├── m6a_dist.csv                        # All 9,826 m6A sites with genomic coordinates
├── m6a_metagene_coord.csv              # Rescaled metagene coordinates for plotting
├── utr3_m6a_dist.csv                   # 3'UTR-specific m6A sites (7,148 sites)
├── utr5_m6a_dist.csv                   # 5'UTR-specific m6A sites (258 sites)
├── m6a_figures.py                      # Full Python analysis script
├── m6A_Fig1_Metagene_Distribution.png
├── m6A_Fig2_Sites_Per_Gene.png
├── m6A_Fig3_Regional_By_Group.png
├── m6A_Fig4_m6A_vs_PolyA_Correlation.png
├── m6A_Fig5_Integrin_Combined.png
└── README.md
```

---

## Methods Summary

| Parameter | Value |
|---|---|
| Cell Line | MDA-231 (Triple-Negative Breast Cancer) |
| Sequencing Platform | Oxford Nanopore MinION |
| Library Kit | SQK-RNA004 (Direct RNA Sequencing) |
| Basecaller | Dorado (modification-aware models) |
| Modifications Detected | N6-methyladenosine (m6A), Pseudouridine (Ψ) |
| Gene Panel | TaqMan Array Micro Fluidic Card 96a |
| Total m6A Sites | 9,826 |
| Genes with m6A Signal | 92/96 (95.8%) |
| Analysis Language | Python (pandas, numpy, matplotlib, scipy) |

m6A modification sites were detected directly from native RNA signal using 
Dorado modification-aware basecalling models. No bisulfite conversion or 
antibody-based pulldown (MeRIP-seq) was required — a key advantage of direct 
RNA nanopore sequencing which preserves native base modifications and avoids 
amplification bias. Metagene coordinates were rescaled to account for variable 
UTR and CDS lengths across genes, enabling comparison of m6A positioning 
across transcripts of different sizes.

---

## How to Reproduce This Analysis

**Requirements:**
- Python 3.8 or higher
- pandas, numpy, matplotlib, scipy

**Install packages:**
```bash
pip install pandas numpy matplotlib scipy
```

**Run analysis:**
```bash
python m6a_figures.py
```

This will generate all five figures in your working directory. Ensure all 
CSV data files are in the same directory as the script.

---

## Data Description

| File | Contents | Rows |
|---|---|---|
| `m6a_dist.csv` | All m6A sites with chr, coord, gene, transcript ID, relative position, UTR/CDS sizes | 9,826 |
| `m6a_metagene_coord.csv` | Rescaled metagene coordinates (0=5'UTR start, 1=CDS start, 2=CDS end, 3=3'UTR end) | 9,826 |
| `utr3_m6a_dist.csv` | Sites in 3'UTR only (rel_location >= 2) | 7,148 |
| `utr5_m6a_dist.csv` | Sites in 5'UTR only (rel_location < 1) | 258 |

---

## Biological Context

**Why m6A matters in cancer:**  
N6-methyladenosine is the most abundant internal modification on mammalian 
mRNA, occurring at an average of 3–5 sites per transcript. m6A is deposited 
by the METTL3/METTL14 writer complex and removed by FTO/ALKBH5 erasers. 
Its effects on RNA fate depend on which reader proteins recognise it:

- **YTHDF2** binds 3'UTR m6A and recruits the CCR4-NOT deadenylase complex, 
  promoting mRNA degradation and polyA tail shortening
- **YTHDF1** promotes cap-independent translation of m6A-modified transcripts
- **YTHDF3** facilitates both degradation and translation depending on context

The strong 3'UTR enrichment observed in this dataset is consistent with 
YTHDF2-mediated decay being the dominant m6A pathway in MDA-231 cells. 
However, the lack of a significant correlation between m6A burden and polyA 
tail length (r=0.109, p=0.372) suggests that YTHDF2 activity is selective 
rather than proportional to site count — certain transcripts may be protected 
from m6A-mediated decay despite carrying modification sites.

**Connection to Project 1 (PolyA Tail Length):**  
The integrin family carries both the longest polyA tails in the TNBC 
transcriptome (Project 1) and significant m6A modification burden (this 
project). Despite their 3'UTR m6A sites — which would predict YTHDF2-mediated 
degradation — integrin transcripts are among the most stable in MDA-231 cells. 
This suggests that integrin mRNAs may resist m6A-mediated decay through 
competitive reader binding (YTHDF1/3 over YTHDF2) or through RNA secondary 
structures that occlude reader access. This is a testable hypothesis for 
future experimental work.

---

## Relationship to Project 1

This repository is the second of two complementary analyses:

| | Project 1 | Project 2 (this repository) |
|---|---|---|
| Measurement | PolyA tail length | m6A modification sites |
| What it captures | Transcript stability outcome | Post-transcriptional regulatory input |
| Key finding | Integrins stabilised; oncogenes short-tailed | 3'UTR dominant; m6A burden independent of polyA length |
| Repository | [polya-tnbc-nanopore](https://github.com/somritaghosh-1/polya-tnbc-nanopore) | This repository |

---

## Future Directions

- Pseudouridine modification analysis from the same MinION sequencing run
- Correlation of m6A site positioning (not just count) with polyA tail length 
  at individual transcript level
- Comparison with PEO1 and PEO4 ovarian cancer cell lines
- YTHDF2 knockdown functional validation of m6A-mediated decay in integrin 
  transcripts
- Integration with TCGA m6A and expression data across 40 cancer types

---

## Contact

**Somrita Ghosh**  
somritaghosh56@gmail.com  
linkedin.com/in/somrita-ghosh-014826211  
GitHub: github.com/somritaghosh-1  
