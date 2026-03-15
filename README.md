# m6A RNA Modification Landscape in Triple-Negative Breast Cancer

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Oxford%20Nanopore%20MinION-0084A9?style=flat-square" alt="Platform">
  <img src="https://img.shields.io/badge/Kit-SQK--RNA004-2E75B6?style=flat-square" alt="Kit">
  <img src="https://img.shields.io/badge/m6A%20Sites-9%2C826-7030A0?style=flat-square" alt="Sites">
  <img src="https://img.shields.io/badge/Cancer%20Genes-92-C00000?style=flat-square" alt="Genes">
  <img src="https://img.shields.io/badge/Language-Python-3776AB?style=flat-square&logo=python" alt="Python">
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square" alt="License">
</p>

<p align="center">
  <strong>Epitranscriptomic Analysis | MDA-231 TNBC | Oxford Nanopore Direct RNA Sequencing</strong><br>
  <em>Somrita Ghosh — MSc Molecular Biology and Biotechnology, Queen's University Belfast (2024)</em><br>
  Patrick G Johnston Centre for Cancer Research | Institute for Global Food Security
</p>

<br>

> **Part 2 of 2** — This repository is the second of two complementary epitranscriptomic analyses. Part 1 covering polyA tail length regulation is available at [polya-tnbc-nanopore](https://github.com/somritaghosh-1/polya-tnbc-nanopore). Together they form the first combined polyA tail length and m6A modification profile of a clinically validated cancer gene panel in triple-negative breast cancer, generated from a single Oxford Nanopore direct RNA sequencing experiment.

<br>

## Table of Contents

- [Overview](#overview)
- [Key Findings](#key-findings)
- [Figures](#figures)
- [Repository Structure](#repository-structure)
- [Methods](#methods)
- [How to Reproduce](#how-to-reproduce)
- [Data Description](#data-description)
- [Biological Context](#biological-context)
- [Relationship to Project 1](#relationship-to-project-1)
- [Future Directions](#future-directions)
- [Citation](#citation)
- [Contact](#contact)

<br>

## Overview

This project maps the N6-methyladenosine (m6A) RNA modification landscape across 92 cancer-associated genes in MDA-231 triple-negative breast cancer (TNBC) cells, using Oxford Nanopore direct RNA sequencing with Dorado modification-aware basecalling.

m6A is the most abundant internal modification on mammalian mRNA. Its effects on transcript fate that is stability, translation, or degradation depends on which reader proteins recognise it. By mapping where m6A sites cluster across transcript regions (5'UTR, CDS, 3'UTR) in a TNBC context, this analysis reveals the post-transcriptional regulatory inputs that, together with polyA tail length data from Project 1, begin to explain how MDA-231 cells maintain constitutive expression of invasion-driving proteins.

**Why this matters:** TNBC lacks oestrogen receptor, progesterone receptor, and HER2 amplification, making it unresponsive to targeted therapies. Understanding post-transcriptional regulation in TNBC may reveal new layers of therapeutic vulnerability.

<br>

## Key Findings

| Finding | Detail |
|---|---|
| **Total m6A sites** | 9,826 sites across 92 cancer genes |
| **3'UTR enrichment** | 72.7% of sites (7,148) in 3'UTR, consistent with YTHDF2-mediated mRNA decay |
| **CDS sites** | 24.6% (2,420 sites), suggesting roles in translation elongation and ribosome pausing |
| **Top modified gene** | THBS1 (418 sites), ITGA3 (396), TIMP3 (345), ABL1 (299), BCL2L1 (289) |
| **Integrin spotlight** | All integrin subunits carry both long polyA tails (Project 1) and significant m6A burden |
| **Cross-layer independence** | Pearson r = 0.109 (p = 0.372), m6A site density does not predict polyA tail length |

### Biological Highlight

Despite carrying 3'UTR m6A sites that would predict YTHDF2-mediated mRNA degradation, integrin transcripts maintain above-average polyA tail lengths as shown in Project 1. This suggests that integrin mRNAs actively resist m6A-mediated decay, possibly through competitive YTHDF1/3 reader binding or RNA secondary structures that occlude YTHDF2 access. This is a directly testable hypothesis via YTHDF2 knockdown.

<br>

## Figures

### Figure 1 — m6A Metagene Distribution Across Transcript Regions

![Metagene Distribution](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig1_Metagene_Distribution.png)

*Kernel density estimate of 9,826 m6A sites plotted at their relative positions across transcript regions. Strong 3'UTR enrichment (72.7%) is consistent with YTHDF2-mediated mRNA decay as the dominant m6A pathway in MDA-231 cells.*

<br>

### Figure 2 — m6A Site Density per Cancer Gene

![m6A Sites Per Gene](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig2_Sites_Per_Gene.png)

*Top 35 cancer genes by total m6A site count, stacked by transcript region. Numbers indicate total sites and percentages show the 3'UTR fraction. THBS1, ITGA3, and TIMP3 carry the highest m6A burden.*

<br>

### Figure 3 — Regional Breakdown by Functional Gene Group

![Regional Breakdown](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig3_Regional_By_Group.png)

*Left panel: Stacked bar chart showing the proportion of m6A sites in each transcript region per functional gene group. Right panel: Dot plot of 3'UTR m6A fraction per group. Cell adhesion (integrin) genes show the highest 3'UTR fraction (93%), despite having the longest polyA tails in Project 1.*

<br>

### Figure 4 — m6A Modification Burden vs PolyA Tail Length

![m6A vs PolyA Correlation](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig4_m6A_vs_PolyA_Correlation.png)

*Scatter plots of total m6A count (left) and 3'UTR m6A count (right) versus mean polyA tail length for 69 genes present in both datasets. The non-significant correlation (r = 0.109, p = 0.372) indicates that m6A site density and polyA tail length operate as largely independent regulatory layers.*

<br>

### Figure 5 — Integrin Family: Combined m6A and PolyA Profile

![Integrin Combined](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig5_Integrin_Combined.png)

*Three-panel figure showing m6A site distribution (left), polyA tail length (centre), and biological interpretation (right) for all detected integrin subunits. All integrins display both above-average polyA tails and significant m6A burden, suggesting multi-layered post-transcriptional stabilisation of invasion drivers in MDA-231.*

<br>

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
├── LICENSE
└── README.md
```

<br>

## Methods

| Parameter | Value |
|---|---|
| Cell Line | MDA-231 (Triple-Negative Breast Cancer) |
| Sequencing Platform | Oxford Nanopore MinION |
| Library Kit | SQK-RNA004 (Direct RNA Sequencing) |
| Basecaller | Dorado (modification-aware models) |
| Modifications Detected | N6-methyladenosine (m6A), Pseudouridine |
| Gene Panel | TaqMan Array Micro Fluidic Card 96a (96 cancer genes) |
| Total m6A Sites Detected | 9,826 |
| Genes with m6A Signal | 92/96 (95.8%) |
| Analysis Language | Python 3 (pandas, numpy, matplotlib, scipy) |

**Key methodological advantage:** m6A modification sites were detected directly from native RNA signal using Dorado modification-aware basecalling. No bisulfite conversion or antibody-based immunoprecipitation (MeRIP-seq) was required. Direct RNA nanopore sequencing preserves native base modifications and avoids amplification bias, enabling simultaneous measurement of m6A, pseudouridine, and polyA tail length from a single experiment.

Metagene coordinates were rescaled to account for variable 5'UTR, CDS, and 3'UTR lengths across genes, enabling direct comparison of m6A positioning across transcripts of different sizes.

<br>

## How to Reproduce

**Requirements**

```
Python >= 3.8
pandas
numpy
matplotlib
scipy
```

**Install packages**

```bash
pip install pandas numpy matplotlib scipy
```

**Run analysis**

```bash
git clone https://github.com/somritaghosh-1/m6a-epitranscriptomics-tnbc.git
cd m6a-epitranscriptomics-tnbc
python m6a_figures.py
```

All five figures will be saved to the working directory. Ensure all CSV data files are in the same directory as the script.

<br>

## Data Description

| File | Description | Rows |
|---|---|---|
| `m6a_dist.csv` | All m6A sites with chromosome, coordinate, gene name, transcript ID, relative position, and UTR/CDS sizes | 9,826 |
| `m6a_metagene_coord.csv` | Rescaled metagene coordinates where 0 = 5'UTR start, 1 = CDS start, 2 = CDS end, 3 = 3'UTR end | 9,826 |
| `utr3_m6a_dist.csv` | 3'UTR-restricted subset (rel_location greater than or equal to 2) | 7,148 |
| `utr5_m6a_dist.csv` | 5'UTR-restricted subset (rel_location less than 1) | 258 |

<br>

## Biological Context

### The m6A Regulatory System

N6-methyladenosine (m6A) is deposited by the METTL3/METTL14 writer complex and removed by FTO/ALKBH5 erasers. Its functional consequences depend on which reader proteins recognise it.

| Reader | Location preference | Function |
|---|---|---|
| **YTHDF2** | 3'UTR | Recruits CCR4-NOT deadenylase, promoting mRNA degradation and polyA shortening |
| **YTHDF1** | 3'UTR and CDS | Promotes cap-independent translation |
| **YTHDF3** | 3'UTR | Context-dependent, either degradation or translation |
| **YTHDC1** | Nuclear | Splicing regulation and nuclear export |

### Key Interpretation

The strong 3'UTR enrichment (72.7%) in this dataset is consistent with YTHDF2-mediated decay being the dominant m6A pathway in MDA-231. However, the non-significant correlation between m6A burden and polyA tail length (r = 0.109, p = 0.372) indicates that YTHDF2 activity is selective rather than proportional to site count. Certain transcripts, particularly the integrins, appear protected from m6A-mediated decay despite carrying modification sites.

### Connection to Project 1

The integrin family presents the most striking cross-project finding. In Project 1, all integrins have above-average polyA tail lengths with the longest tails in the dataset. In Project 2, all integrins carry significant 3'UTR m6A burden at a 93% 3'UTR fraction. Despite their 3'UTR m6A sites predicting YTHDF2-mediated degradation, integrin transcripts are among the most stable in MDA-231 cells. This apparent contradiction suggests that integrin mRNAs resist m6A-mediated decay, possibly through competitive YTHDF1/3 over YTHDF2 binding, or RNA secondary structures that occlude reader access to modification sites.

<br>

## Relationship to Project 1

| | [Project 1 — PolyA Tail Length](https://github.com/somritaghosh-1/polya-tnbc-nanopore) | Project 2 — m6A Modification (this repository) |
|---|---|---|
| **Measurement** | PolyA tail length per transcript | m6A modification site positions |
| **What it captures** | Transcript stability outcome | Post-transcriptional regulatory input |
| **Scale** | 247,258 individual reads | 9,826 modification sites |
| **Key finding** | Integrins stabilised; oncogenes short-tailed | 3'UTR dominant; m6A burden independent of polyA length |
| **Tools** | R (ggplot2, dplyr, tidyr) | Python (pandas, matplotlib, scipy) |

Project 1 measures which transcripts are stable. Project 2 maps where m6A sites sit that could regulate that stability. The non-significant correlation between the two layers suggests that post-transcriptional regulation in TNBC is multi-factorial. PolyA tail length and m6A modification operate with substantial independence, meaning neither layer alone is sufficient to predict transcript fate.

<br>

## Future Directions

- [ ] Pseudouridine modification analysis from the same MinION sequencing run (Dorado output available)
- [ ] Per-site m6A positioning analysis (not just count) correlated with polyA tail length at individual transcript level
- [ ] Comparison with PEO1 and PEO4 ovarian cancer cell lines (preliminary data collected during MSc)
- [ ] YTHDF2 knockdown functional validation of m6A-mediated decay resistance in integrin transcripts
- [ ] Integration with TCGA pan-cancer m6A and expression data across 40 cancer types
- [ ] Biological replicates and comparison with normal breast epithelial cell lines

<br>

## Citation

If you use this data or analysis in your research, please cite:

```
Ghosh, S. (2024). m6A RNA Modification Landscape in Triple-Negative Breast Cancer.
MSc Research Project, Queen's University Belfast.
GitHub: https://github.com/somritaghosh-1/m6a-epitranscriptomics-tnbc
```

<br>

## Contact

**Somrita Ghosh**
MSc Molecular Biology and Biotechnology | Queen's University Belfast

[![Email](https://img.shields.io/badge/Email-somritaghosh56%40gmail.com-D14836?style=flat-square&logo=gmail)](mailto:somritaghosh56@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Somrita%20Ghosh-0077B5?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/somrita-ghosh-014826211)
[![GitHub](https://img.shields.io/badge/GitHub-somritaghosh--1-181717?style=flat-square&logo=github)](https://github.com/somritaghosh-1)


<p align="center">
  <sub>Data generated at Queen's University Belfast | Patrick G Johnston Centre for Cancer Research | 2024</sub>
</p>
