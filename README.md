# m6A RNA Modification Landscape in Triple-Negative Breast Cancer
 
<p align="center">
  <img src="https://img.shields.io/badge/Platform-Oxford%20Nanopore%20MinION-0084A9?style=flat-square" alt="Platform">
  <img src="https://img.shields.io/badge/Kit-SQK--RNA004-2E75B6?style=flat-square" alt="Kit">
  <img src="https://img.shields.io/badge/m6A%20Sites-9%2C826-703A00?style=flat-square" alt="Sites">
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
- [Limitations](#limitations)
- [Relationship to Project 1](#relationship-to-project-1)
- [Future Directions](#future-directions)
- [Citation](#citation)
- [Contact](#contact)
 
<br>
 
## Overview
 
This project maps the N6-methyladenosine (m6A) RNA modification landscape across 92 cancer-associated genes in MDA-231 triple-negative breast cancer (TNBC) cells, using Oxford Nanopore direct RNA sequencing with Dorado modification-aware basecalling.
 
m6A is the most abundant internal modification on mammalian mRNA. Its functional consequences — mRNA stabilisation, translation, or degradation — depend on which reader proteins recognise the modification. By mapping where m6A sites cluster across transcript regions (5'UTR, CDS, 3'UTR) in a TNBC context, this analysis reveals the post-transcriptional regulatory inputs that, together with polyA tail length data from Project 1, begin to explain how MDA-231 cells maintain constitutive expression of invasion-driving proteins.
 
**Why this matters:** TNBC lacks oestrogen receptor, progesterone receptor, and HER2 amplification, making it unresponsive to targeted therapies. It accounts for 15–20% of breast cancer diagnoses and carries the worst prognosis of any breast cancer subtype. Understanding post-transcriptional regulation in TNBC may reveal new layers of therapeutic vulnerability not accessible to standard transcriptomic approaches.
 
<br>
 
## Key Findings
 
| Finding | Detail |
|---|---|
| **Total m6A sites** | 9,826 sites across 92 cancer genes |
| **3'UTR enrichment** | 72.7% of sites (7,148) in 3'UTR, consistent with YTHDF2-mediated mRNA decay |
| **CDS sites** | 24.6% (2,420 sites), suggesting roles in translation elongation and ribosome pausing |
| **Top modified gene** | THBS1 (418 sites), ITGA3 (396), TIMP3 (345), ABL1 (299), BCL2L1 (289) |
| **Gene-level heterogeneity** | Top modified genes vary substantially in 3'UTR fraction: THBS1 57.4%, ABL1 50.5%, MYC 30.7% vs ITGA2 97.6%, SERPINE1 98.7% |
| **Integrin m6A burden** | All six detected integrin subunits carry significant m6A sites, predominantly in 3'UTR (84–100%) |
| **Cross-layer independence** | Pearson r = 0.109 (p = 0.372): m6A site density does not predict polyA tail length |
 
### Biological Highlights
 
**3'UTR dominance with gene-level heterogeneity:** The dataset-wide 3'UTR enrichment (72.7%) is consistent with YTHDF2-mediated mRNA decay as the dominant m6A pathway in MDA-231. However, this masks substantial gene-level variation. THBS1, the most heavily modified gene (418 sites), has only 57.4% of sites in the 3'UTR with 178 CDS sites — suggesting a translation-regulatory role in addition to stability control. Similarly, MYC (30.7% 3'UTR), ABL1 (50.5%), and JUN (38.9%) carry majority CDS m6A burden, consistent with m6A-driven regulation of translation elongation rather than mRNA decay for these oncogenes.
 
**The integrin paradox:** All six detected integrin subunits (ITGB1, ITGA1, ITGA2, ITGA3, ITGAV, ITGB5) carry significant 3'UTR m6A burden (84–100% 3'UTR fraction). Under YTHDF2-mediated decay, this predicts mRNA destabilisation and polyA shortening. Yet Project 1 shows that five of these integrins maintain above-average polyA tail lengths. This contradiction — high 3'UTR m6A burden combined with mRNA stabilisation — suggests that integrin mRNAs actively resist m6A-mediated decay, possibly through competitive YTHDF1/3 reader binding or RNA secondary structures that occlude YTHDF2 access. This is a directly testable hypothesis via YTHDF2 knockdown.
 
**Cross-layer independence:** The non-significant Pearson correlation between m6A site density and polyA tail length (r = 0.109, p = 0.372, n = 69 genes) indicates that these two post-transcriptional regulatory layers operate largely independently in MDA-231. Neither layer alone is sufficient to predict transcript fate.
 
<br>
 
## Figures
 
### Figure 1 — m6A Metagene Distribution Across Transcript Regions
 
![Metagene Distribution](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig1_Metagene_Distribution.png)
 
*Kernel density estimate of 9,826 m6A sites plotted at their relative positions across transcript regions (0–1 = 5'UTR, 1–2 = CDS, 2–3 = 3'UTR). Strong 3'UTR enrichment (72.7%) is consistent with YTHDF2-mediated mRNA decay as the dominant m6A pathway in MDA-231 cells. Metagene coordinates are rescaled to account for variable UTR and CDS lengths across genes.*
 
<br>
 
### Figure 2 — m6A Site Density per Cancer Gene
 
![m6A Sites Per Gene](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig2_Sites_Per_Gene.png)
 
*Top 35 cancer genes by total m6A site count, stacked by transcript region (3'UTR, CDS, 5'UTR). Numbers indicate total sites; percentages show the 3'UTR fraction. Note the heterogeneity in regional distribution: THBS1 and ABL1 carry substantial CDS burden alongside 3'UTR sites, while ITGA2, SERPINE1, and ITGA1 are almost exclusively 3'UTR-modified.*
 
<br>
 
### Figure 3 — Regional Breakdown by Functional Gene Group
 
![Regional Breakdown](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig3_Regional_By_Group.png)
 
*Left panel: Stacked bar chart showing the proportion of m6A sites in each transcript region per functional gene group. Right panel: Dot plot of 3'UTR m6A fraction per group. Cell adhesion (integrin) genes show the highest 3'UTR fraction (93%), despite maintaining above-average polyA tail lengths in Project 1.*
 
<br>
 
### Figure 4 — m6A Modification Burden vs PolyA Tail Length
 
![m6A vs PolyA Correlation](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig4_m6A_vs_PolyA_Correlation.png)
 
*Scatter plots of total m6A count (left) and 3'UTR m6A count (right) versus mean polyA tail length for 69 genes present in both datasets. The non-significant correlation (r = 0.109, p = 0.372) indicates that m6A site density and polyA tail length operate as largely independent regulatory layers in MDA-231.*
 
<br>
 
### Figure 5 — Integrin Family: Combined m6A and PolyA Profile
 
![Integrin Combined](https://raw.githubusercontent.com/somritaghosh-1/m6a-epitranscriptomics-tnbc/main/m6A_Fig5_Integrin_Combined.png)
 
*Three-panel figure showing m6A site distribution (left), polyA tail length from Project 1 (centre), and biological interpretation (right) for all detected integrin subunits. All integrins carry predominantly 3'UTR m6A sites that predict YTHDF2-mediated decay, yet five of six maintain above-average polyA tail lengths — suggesting active resistance to m6A-mediated destabilisation.*
 
<br>
 
## Repository Structure
 
```
m6a-epitranscriptomics-tnbc/
├── m6a_dist.csv                        # All 9,826 m6A sites with genomic coordinates
├── m6a_metagene_coord.csv              # Rescaled metagene coordinates for plotting
├── utr3_m6a_dist.csv                   # 3'UTR-specific m6A sites (7,148 sites)
├── utr5_m6a_dist.csv                   # 5'UTR-specific m6A sites (258 sites)
├── cds_m6a_dist.csv                    # CDS-specific m6A sites (2,420 sites)
├── temp_df.csv                         # Transcript annotation lookup (gene name, Ensembl ID, length)
├── trx_len.csv                         # Full transcript length distribution for metagene scaling
├── utr3_SF.csv                         # 3'UTR metagene scaling factor (1.1471)
├── utr5_SF.csv                         # 5'UTR metagene scaling factor (0.1456)
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
| Basecaller | Dorado (modification-aware, `--modified-bases m6A_DRACH`) |
| Modifications Detected | N6-methyladenosine (m6A), Pseudouridine (Ψ) |
| Gene Panel | TaqMan Array Micro Fluidic Card 96a (96 cancer genes) |
| Total m6A Sites | 9,826 |
| Genes with m6A Signal | 92/96 (95.8%) |
| Analysis Language | Python 3 (pandas, numpy, matplotlib, scipy) |
 
### Cell culture
 
MDA-MB-231 cells were maintained in DMEM supplemented with 10% FBS and 1% penicillin/streptomycin at 37°C with 5% CO₂. Cells were confirmed mycoplasma-negative prior to RNA extraction. RNA was extracted using TRIzol following the manufacturer's protocol.
 
### Step 1 — Basecalling with Dorado (modification-aware)
 
Raw Oxford Nanopore POD5 signal files were basecalled using Dorado with a modification-aware model to simultaneously detect polyA tail length, m6A, and pseudouridine from native RNA signal. No bisulfite conversion or antibody-based immunoprecipitation (MeRIP-seq) was required.
 
```bash
dorado basecaller \
  rna004_130bps_sup@v5.0.0 \
  /path/to/pod5_files/ \
  --modified-bases m6A_DRACH \
  --emit-moves \
  > calls.bam
```
 
`--modified-bases m6A_DRACH` restricts m6A detection to the DRACH consensus motif, the canonical recognition sequence of the METTL3/METTL14 writer complex.
 
### Step 2 — Alignment to Reference Transcriptome
 
Basecalled reads were aligned to the human reference transcriptome (Ensembl GRCh38) using minimap2 in splice-aware RNA mode:
 
```bash
minimap2 \
  -ax splice \
  -uf \
  --secondary=no \
  GRCh38_transcriptome.fa \
  calls.bam \
  | samtools sort -O bam -o aligned.bam
 
samtools index aligned.bam
```
 
Transcript annotation was drawn from Ensembl GRCh38. The 92 genes with m6A signal were matched to their primary Ensembl transcript IDs (e.g. ITGB1 → ENST00000302278.8; JUN → ENST00000371222.4). Transcript lengths ranged from 563 nt (S100A4) to 3,732 nt (ITGB1).
 
### Step 3 — m6A Site Pileup with Modkit
 
Modified base pileup was performed using ONT Modkit (`modkit pileup`), which aggregates per-read m6A calls across reference positions into site-level counts:
 
```bash
modkit pileup \
  aligned.bam \
  m6a_pileup.bed \
  --mod-thresholds a:0.5 \
  --log-filepath modkit_pileup.log
```
 
`--mod-thresholds a:0.5` retains only m6A calls with posterior probability ≥ 0.5. This is the primary quality filter separating true modification signal from basecalling noise. Output is bedMethyl format with per-position N_mod, N_canonical, N_valid_cov, and fraction_modified.
 
### Step 4 — Site Filtering and Gene Assignment
 
m6A sites were intersected with annotated transcript regions using Ensembl GRCh38 GTF coordinates. Each site was assigned a `rel_location` value:
 
- `rel_location < 1`: 5'UTR → 258 sites (`utr5_m6a_dist.csv`)
- `1 ≤ rel_location < 2`: CDS → 2,420 sites (`cds_m6a_dist.csv`)
- `rel_location ≥ 2`: 3'UTR → 7,148 sites (`utr3_m6a_dist.csv`)
 
Total retained sites: **9,826** across 92 genes (`m6a_dist.csv`).
 
### Step 5 — Metagene Coordinate Rescaling
 
Each site's coordinate was rescaled to a normalised metagene position to enable comparison across transcripts of different lengths:
 
- 5'UTR: offset = 0, scaling factor = 0.1456 (`utr5_SF.csv`)
- CDS: offset = 1, scaling factor = 1.0
- 3'UTR: offset = 2, scaling factor = 1.1471 (`utr3_SF.csv`)
 
Rescaled coordinates are stored in `m6a_metagene_coord.csv` and used for Figure 1.
 
### Step 6 — Downstream Analysis in Python
 
All figures and statistics were generated using `m6a_figures.py`. Key analyses:
 
- **Figure 1:** KDE of metagene coordinates using `scipy.stats.gaussian_kde`
- **Figure 2:** Per-gene m6A site counts stacked by region
- **Figure 3:** Regional breakdown by functional gene group
- **Figure 4:** Pearson correlation of m6A count vs mean polyA tail length (cross-project)
- **Figure 5:** Integrin-specific combined m6A and polyA panel
 
### Software versions
 
| Tool | Purpose |
|---|---|
| Dorado ≥ 0.7.0 | Basecalling + m6A detection |
| minimap2 2.26 | Alignment |
| samtools 1.18 | BAM handling |
| Modkit ≥ 0.3.0 (ONT) | m6A pileup |
| Python ≥ 3.8 | Analysis and figures |
| pandas, numpy, matplotlib, scipy | Data handling, statistics, visualisation |
 
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
| `m6a_dist.csv` | All 9,826 m6A sites: chromosome, coordinate, gene name, Ensembl transcript ID, rel_location, UTR/CDS boundary coordinates | 9,826 |
| `m6a_metagene_coord.csv` | Rescaled metagene coordinate (x) for each site. Coordinate space: 0–1 = 5'UTR, 1–2 = CDS, 2–3 = 3'UTR | 9,826 |
| `utr3_m6a_dist.csv` | 3'UTR-restricted subset (rel_location ≥ 2) | 7,148 |
| `utr5_m6a_dist.csv` | 5'UTR-restricted subset (rel_location < 1) | 258 |
| `cds_m6a_dist.csv` | CDS-restricted subset (1 ≤ rel_location < 2) | 2,420 |
| `temp_df.csv` | Transcript annotation lookup: gene name, Ensembl transcript ID, transcript length for 92 genes | 92 |
| `trx_len.csv` | Full transcript length distribution used in metagene scaling | 38,906 |
| `utr3_SF.csv` | 3'UTR metagene scaling factor (1.1471) | 1 |
| `utr5_SF.csv` | 5'UTR metagene scaling factor (0.1456) | 1 |
 
**Four genes produced no detectable m6A signal:** CDKN2A, IFNA1, IFNB1, and one additional panel gene below detection threshold. CDKN2A is frequently deleted or epigenetically silenced in MDA-231.
 
<br>
 
## Biological Context
 
### The m6A regulatory system
 
N6-methyladenosine (m6A) is deposited by the METTL3/METTL14 writer complex and removed by FTO/ALKBH5 erasers. Its functional consequences depend on which reader proteins recognise it:
 
| Reader | Location preference | Function |
|---|---|---|
| **YTHDF2** | 3'UTR | Recruits CCR4-NOT deadenylase — promotes mRNA degradation and polyA shortening |
| **YTHDF1** | 3'UTR and CDS | Promotes cap-independent translation |
| **YTHDF3** | 3'UTR | Context-dependent: degradation or translation enhancement |
| **YTHDC1** | Nuclear | Splicing regulation and nuclear export |
 
### Dataset-level interpretation
 
The strong 3'UTR enrichment (72.7%) is consistent with YTHDF2-mediated decay being the dominant m6A pathway in MDA-231. However, the non-significant correlation between m6A burden and polyA tail length (r = 0.109, p = 0.372) indicates that YTHDF2 activity is selective rather than proportional to site count — certain transcripts appear protected from m6A-mediated decay despite carrying 3'UTR modification sites.
 
### Gene-level heterogeneity
 
The dataset-wide 3'UTR dominance conceals important gene-level variation. THBS1 (418 sites total, 57.4% 3'UTR) and ABL1 (299 sites, 50.5% 3'UTR) carry substantial CDS m6A burden alongside their 3'UTR sites, implicating translation elongation regulation in addition to mRNA stability control. MYC (153 sites, 30.7% 3'UTR) and JUN (239 sites, 38.9% 3'UTR) are predominantly CDS-modified, consistent with m6A influencing oncogene translation rather than mRNA decay. By contrast, ITGA2 (97.6% 3'UTR), SERPINE1 (98.7%), and ITGA1 (100%) are almost exclusively 3'UTR-modified.
 
### The integrin paradox
 
All six detected integrin subunits carry predominantly 3'UTR m6A sites (84–100% 3'UTR fraction). Under canonical YTHDF2-mediated decay, this predicts mRNA destabilisation. Yet Project 1 shows five of six integrins maintain above-average polyA tails (ITGB1 at 143.0 nt, ITGA1 at 134.7 nt, ITGA2 at 134.7 nt, ITGA3 at 122.0 nt, ITGAV at 167.2 nt). This apparent contradiction suggests integrin mRNAs resist m6A-mediated decay through competitive YTHDF1/3 over YTHDF2 binding, or RNA secondary structures that occlude reader access. This is a directly testable hypothesis via YTHDF2 knockdown followed by polyA tail profiling.
 
<br>
 
## Limitations
 
- **Single cell line, single run, no biological replicates.** All data derive from one sequencing experiment on MDA-231. Findings cannot be generalised to primary TNBC tumours without further validation.
- **No normal comparator.** There is no matched normal breast epithelial dataset. It is not possible to determine which m6A patterns are TNBC-specific versus general features of cultured epithelial cells.
- **m6A calls are probability-threshold dependent.** Sites were retained at Dorado posterior probability ≥ 0.5. Sites near this threshold may include false positives; raising the threshold would reduce sensitivity. The optimal threshold for direct RNA m6A calling is an active area of methodological development.
- **Site count ≠ modification stoichiometry.** This analysis counts the number of genomic positions with m6A signal per gene, not the fraction of transcripts modified at each site. High site count could reflect either many low-stoichiometry sites or fewer high-stoichiometry sites.
- **Functional interpretation is correlative.** Reader protein identity (YTHDF1/2/3) driving each site's functional consequence is inferred from known biology and requires experimental validation.
- **96-gene panel design.** The TaqMan Array Micro Fluidic Card 96a was designed for expression profiling. Panel composition may introduce ascertainment bias toward well-characterised cancer genes.
 
<br>
 
## Relationship to Project 1
 
|  | [Project 1 — PolyA Tail Length](https://github.com/somritaghosh-1/polya-tnbc-nanopore) | Project 2 — m6A Modification (this repository) |
|---|---|---|
| **What it measures** | PolyA tail length per read per transcript | m6A modification site positions across transcript regions |
| **What it captures** | Transcript stability outcome | Post-transcriptional regulatory input |
| **Scale** | 247,258 individual reads across 88 genes | 9,826 modification sites across 92 genes |
| **Key finding** | Five integrins stabilised; TGF-beta1 and key oncogenes short-tailed | 3'UTR dominant (72.7%); m6A burden independent of polyA length (r = 0.109, p = 0.372) |
| **Analysis language** | R (ggplot2, dplyr, tidyr) | Python (pandas, matplotlib, scipy) |
 
Project 1 measures which transcripts are stable. Project 2 maps where m6A sites sit that could regulate that stability. The non-significant cross-project correlation indicates that polyA tail length and m6A modification burden are largely independent post-transcriptional regulatory layers in MDA-231. The integrin family — long polyA tails in Project 1, high 3'UTR m6A burden in Project 2, apparent resistance to m6A-mediated decay — presents the most biologically compelling finding from the combined analysis.
 
<br>
 
## Future Directions
 
- [ ] Pseudouridine modification analysis from the same MinION sequencing run (Dorado output available)
- [ ] YTHDF2 knockdown to functionally validate m6A-mediated decay resistance in integrin transcripts
- [ ] Per-site m6A stoichiometry analysis (fraction modified per site, not just site count)
- [ ] Comparison with PEO1 and PEO4 ovarian cancer cell lines (preliminary data collected during MSc)
- [ ] Comparison with normal breast epithelial cells (MCF-10A) to identify TNBC-specific m6A patterns
- [ ] Biological replicates (≥3) to confirm site-level m6A calls
- [ ] Integration with TCGA pan-cancer m6A writer/eraser expression data across 40 cancer types
 
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
 
