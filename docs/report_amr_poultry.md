# One Health Assessment of Microbial Dynamics and Predicted Antimicrobial-Resistance Pathways Across Poultry Farm, Cattle Farm, and Hospital Environments and Farm Workers in Bangladesh

**A cross-sectional, comparative One Health 16S rRNA (V3–V4) amplicon study**

*Analysis report — project `amr_poultry` · DeepBio Academy · 2026-08-31*

---

## Abstract

Antimicrobial resistance (AMR) propagates across the environment–animal–human interface, yet integrated surveillance that spans livestock and clinical compartments in low- and middle-income settings remains scarce. We profiled bacterial communities and their **predicted** AMR functional potential across three One Health compartments — a poultry farm, a cattle farm, and a hospital — using 14 Illumina MiSeq 16S rRNA (V3–V4) samples: paired farm effluent and worker hand-rinse samples (poultry, 4 pairs; cattle, 2 pairs) and hospital effluent (n = 2). DADA2 resolved 5,520 bacterial amplicon sequence variants (ASVs). Bacterial community structure was driven far more strongly by **sample type (effluent vs. hand-rinse)** than by compartment, a pattern mirrored in the PICRUSt2-predicted resistome (sample type R² = 0.22, p = 0.035; site not significant). *Acinetobacter* dominated every compartment (19–58% relative abundance), and a **35-genus core** — including *Acinetobacter*, *Aeromonas*, *Escherichia-Shigella*, *Klebsiella*, *Enterobacter*, *Enterococcus*, *Pseudomonas*, *Citrobacter*, and *Salmonella* — was shared across all three compartments. Community-level source analysis — both descriptive (shared-taxa Bray-Curtis) and formal (SourceTracker2 Bayesian mixture model) — did **not** detect consistent farm-specific effluent→worker sourcing; instead, poultry workers' hands carried a low-diversity, *Acinetobacter*-rich community sourced predominantly from cattle and hospital effluent (SourceTracker2: 15–87% hospital, 6–50% cattle, ≤8.6% poultry), while one cattle pair showed near-complete effluent–hand sourcing (95.3%). The two methods strongly concurred (Spearman ρ = 0.872). Predicted resistome potential was dominated by beta-lactam, multidrug-efflux, and aminoglycoside classes. All resistome results are **predicted functional potential**, not detected resistance genes. Findings are hypothesis-generating and motivate shotgun-metagenomic and culture-based confirmation.

---

## 1. Introduction and literature context

Livestock production is a recognized amplifier of AMR, and Bangladesh's dense poultry sector — combined with close, often unprotected, worker contact and direct effluent discharge — creates a high-risk environment–human transmission interface [1, 13]. Metagenomic surveys of Bangladeshi poultry environments have begun to characterize these communities [1, 5], and resistome studies confirm overlapping human, animal, and wastewater resistance gene pools in the country [4, 7, 8]. However, the evidence base has three gaps that motivated the present design:

1. **Single-compartment focus.** Existing Bangladesh poultry studies profile the farm environment alone [1] or integrated chicken–fish systems [5]; none compare poultry, cattle, **and** hospital effluent within one sampling and sequencing design. Cattle in particular are an under-represented livestock comparator.
2. **Paired environment↔worker whole-community profiling is rare in LMICs.** Worker exposure is usually inferred from questionnaires or targeted isolates [13] rather than from paired, whole-community effluent and hand-rinse microbiomes.
3. **Cross-compartment predicted-resistome comparison is missing for Bangladesh.** Resistome work has focused on fecal/wastewater gene overlap [7, 8] or single-setting wastewater [34], not a farm–worker–clinical comparison.

Methodologically, strain-resolved shotgun/MAG approaches set the benchmark for confirming poultry→worker ARG transmission [15, 31]; 16S amplicon data cannot reach that resolution and instead provide community-level, predictive inference. This study was therefore framed — given the available 16S data — as a **comparative One Health** survey of microbial community structure and *predicted* AMR functional potential across the three compartments, with an explicit, honestly-bounded treatment of transmission.

## 2. Objectives

1. Compare bacterial community composition and diversity across poultry farm, cattle farm, and hospital compartments, and between effluent and worker hand-rinse sample types.
2. Identify AMR-relevant / pathogen-risk genera and any cross-compartment shared ("core") taxa.
3. Predict and compare the functional resistome (AMR drug-class potential) across compartments and sample types using PICRUSt2 mapped to KEGG's curated antimicrobial-resistance gene hierarchy.
4. Evaluate community-level evidence for environment→worker and farm↔hospital sharing, framed as inferential rather than strain-confirmed.

## 3. Methods

**Samples and sequencing.** Fourteen samples spanning three compartments: poultry farm (4 effluent + 4 worker hand-rinse; pairs P1–P4), cattle farm (2 effluent + 2 hand-rinse; pairs C1–C2), and hospital (2 effluent; H1–H2, no hand-rinse). Illumina MiSeq 2×300 bp targeting the 16S V3–V4 region (primers 341F `CCTACGGGNGGCWGCAG` / 806R `GACTACHVGGGTATCTAATCC`; ~420 bp amplicon).

**Bioinformatics.** Primers were removed with Cutadapt; reads were processed in R with **DADA2** (`truncLen = c(260,200)`, `maxEE = c(3,8)`, `truncQ = 2`, `minLen = 150`, PhiX removed; `mergePairs` `minOverlap = 12`, `maxMismatch = 1`; amplicon-length filter 390–440 bp; chimera removal). These parameters were chosen after QC showed reverse-read quality collapsing after ~180 bp. Taxonomy was assigned against **SILVA v138.1** with species-level assignment; a DECIPHER alignment and FastTree phylogeny were built for phylogenetic metrics. A phyloseq object was constructed for downstream analysis. (QIIME2-equivalent workflow implemented in R for provisioning speed; scientifically equivalent.)

**Diversity and differential abundance.** Alpha diversity (Observed ASVs, Shannon, Pielou evenness, Faith's PD) was compared by Kruskal–Wallis with Benjamini–Hochberg correction. Beta diversity (Bray–Curtis, weighted and unweighted UniFrac) was tested by PERMANOVA with PERMDISP dispersion checks. Differentially abundant genera were screened with **ALDEx2** (site: Kruskal–Wallis; sample type: Welch's t / Wilcoxon). AMR-relevant genera were curated a priori (WHO/priority-pathogen–relevant genera).

**Predicted resistome.** **PICRUSt2** predicted KEGG Ortholog (KO) abundances per sample (8,486 KOs; per-sample weighted NSTI 0.030–0.099, all well below the 0.15 reliability cutoff). Predicted KOs were mapped to AMR drug classes using **KEGG BRITE ko01504 (antimicrobial-resistance genes)** — 238 curated AMR KOs across 13 classes, including the multidrug-efflux, glycopeptide, cationic-antimicrobial-peptide (CAMP), and beta-lactam resistance modules expanded to constituent KOs. Per-class abundance = summed relative abundance of member KOs. Classes were compared by Kruskal–Wallis, and the resistome profile by PERMANOVA (Bray–Curtis).

**Source / sharing analysis.** For each worker hand-rinse (sink), shared ASVs, Jaccard overlap, abundance-weighted shared fraction, and Bray–Curtis similarity were computed against every effluent sample (candidate sources). The paired farm effluent was contrasted with cross-compartment effluent using paired one-sided Wilcoxon tests. Hospital↔farm sharing was quantified as ASVs shared between hospital effluent and each farm sample. Additionally, **SourceTracker2** (v2.0.1; Bayesian Gibbs-sampling mixture model) was applied with all 8 effluent samples as candidate sources (3 source categories: Cattle farm, Poultry farm, Hospital effluent) and 6 worker hand-rinse samples as sinks, using 10 restarts, 100 burnin passes, and rarefaction depth 10,000. SourceTracker2 proportions were compared against the descriptive shared-taxa metrics using Spearman correlation.

**Reproducibility.** Full code, parameters, and outputs are in the session execution notebook; QC in `qc_multiqc_report.html`.

## 4. Results

### 4.1 Sequencing and ASV inference
After quality trimming, denoising, merging, and chimera removal, samples retained **19,129–42,327 non-chimeric reads** (≈20–42% of raw input; Table 1), yielding **5,523 ASVs** (5,520 bacterial). Retention was limited by reverse-read quality, an expected property of 2×300 V3–V4 data.

### 4.2 Community composition (Fig. 2a/b)
Effluent samples were diverse and dominated by *Proteobacteria*, *Bacteroidota*, *Firmicutes*, and *Campylobacterota*; poultry effluent was notably *Arcobacter*-rich. Worker hand-rinse samples were far less diverse and dominated by *Acinetobacter*. Genus-level profiles (Fig. 2b) show the effluent-vs-hand contrast clearly within each compartment.

### 4.3 Alpha diversity (Fig. 3; Table 2)
Richness and phylogenetic diversity differed significantly by **sample type** (Observed p = 0.0045, q = 0.009; Faith's PD p = 0.0019, q = 0.0078), with effluent > hand-rinse. Community structure/evenness differed by **site** (Shannon p = 0.012, q = 0.024; Pielou p = 0.0076, q = 0.024). Poultry hand-rinse samples had the lowest richness (Observed 244–361).

### 4.4 Beta diversity (Fig. 4; Table 3a)
**Sample type** was the consistent, strong driver across all three distance metrics — Bray–Curtis R² = 0.126 (p = 0.014), weighted UniFrac R² = 0.269 (p = 0.0012), unweighted UniFrac R² = 0.244 (p = 0.0005). **Site** was marginal and only significant for Bray–Curtis (R² = 0.196, p = 0.050); PERMDISP was non-significant for site (p = 0.247), supporting a true location effect rather than dispersion. In short, *what* the sample is (effluent vs. hand) matters more than *where* it came from.

### 4.5 AMR-relevant / pathogen-risk genera (Fig. 5; Table 5)
***Acinetobacter* dominated every compartment**: poultry hand 58.2%, hospital effluent 39.7%, cattle effluent 39.0%, cattle hand 37.6%, poultry effluent 19.2%. Other notable signals: *Aeromonas* 18.8% in poultry hand; *Arcobacter* 18.7% in poultry effluent and 5.5% in hospital effluent; *Escherichia-Shigella* 8.7% in poultry hand and 6.6% in hospital effluent; *Corynebacterium* ~8% in cattle samples; *Klebsiella* 4.8% in cattle hand; *Streptococcus* 4.4% in hospital effluent. No genus reached ALDEx2 significance at BH q < 0.05 (expected given n = 14); top-ranked genera are reported in Table 4.

### 4.6 Cross-compartment core (Table 7)
A **35-genus core was shared across all three compartments**, dominated by *Acinetobacter* (≈36–38% mean relative abundance in each) and including *Aeromonas*, *Escherichia-Shigella*, *Flavobacterium*, *Corynebacterium*, *Enterobacter*, *Klebsiella*, *Enterococcus*, *Pseudomonas*, *Bacteroides*, *Stenotrophomonas*, *Citrobacter*, *Salmonella*, and *Cronobacter*. This shared reservoir spans the environment–worker–clinical interface.

### 4.7 Predicted resistome (Fig. 6; Tables 3b, 6)
Thirteen AMR classes were predicted, led by **beta-lactam** (40 KOs), **multidrug efflux** (48 KOs), **aminoglycoside** (27), **macrolide** (17), **glycopeptide** (16), **tetracycline** (11), and **CAMP** (12). Mirroring the taxonomic pattern, the resistome profile differed by **sample type** (PERMANOVA R² = 0.219, p = 0.035) but **not by site** (R² = 0.056, p = 0.945). By sample type, quinolone (p = 0.0045), beta-lactam (p = 0.0098), sulfonamide (p = 0.020), and CAMP (p = 0.039) classes differed nominally (none passed BH q < 0.05; closest q ≈ 0.059–0.064). **These are predicted functional potentials, not detected ARGs.**

### 4.8 Source / sharing analysis (Fig. 7, 7b, 8; Tables 8, 9)

**4.8.1 Shared-taxa analysis (descriptive).** Across all six effluent→worker pairs there was **no consistent farm-specific sourcing** (paired vs. cross-compartment Wilcoxon one-sided p = 0.72–0.84). The pattern split sharply by compartment:
- **Cattle pair C1** showed near-complete effluent–hand overlap (Bray–Curtis similarity 0.89; the paired effluent ranked #1 of 8 candidate sources).
- **Poultry pairs P1–P4** showed the opposite: hand communities were *less* similar to their own farm's effluent (Bray–Curtis 0.003–0.017; ranks 5–8) than to cross-compartment effluent, because poultry hands are *Acinetobacter*-dominated and thus resemble the *Acinetobacter*-rich cattle and hospital effluents more than the *Arcobacter*-rich poultry effluent.

Hospital↔farm sharing was substantial: each farm sample shared **100–335 ASVs** with hospital effluent (Fig. 7b), consistent with the 35-genus core.

**4.8.2 Formal source tracking (SourceTracker2).** To quantify effluent-vs-other source proportions per worker, we applied **SourceTracker2** (Bayesian Gibbs-sampling mixture model; 10 restarts, 100 burnin, rarefaction depth 10,000) with all 8 effluent samples as candidate sources (grouped into 3 source categories: Cattle farm effluent, Poultry farm effluent, Hospital effluent) and each of the 6 worker hand-rinse samples as sinks. The model also estimates an "Unknown" source representing communities not explained by any training source.

The formal model **strongly corroborated the shared-taxa analysis** (Fig. 8; Table 9):

| Worker | Top source | Cattle eff. | Poultry eff. | Hospital eff. | Unknown |
|--------|-----------|------------|-------------|--------------|---------|
| CH1 (Cattle) | Cattle effluent | **95.3%** | 0.03% | 0.3% | 4.4% |
| CH2 (Cattle) | Hospital effluent | 20.9% | 0.06% | **48.9%** | 30.2% |
| PH1 (Poultry) | Hospital effluent | 20.2% | 0.01% | **66.3%** | 13.5% |
| PH2 (Poultry) | Cattle effluent | **50.2%** | 8.6% | 15.2% | 26.0% |
| PH3 (Poultry) | Hospital effluent | 18.5% | 0.02% | **73.2%** | 8.3% |
| PH4 (Poultry) | Hospital effluent | 5.9% | 0.003% | **87.2%** | 7.0% |

Key findings:
- **Poultry farm effluent contributed negligibly (0.003–8.6%) to all poultry workers' hand communities.** Instead, hospital effluent (15–87%) and cattle effluent (6–50%) were the dominant predicted sources.
- **Cattle pair C1** was sourced 95.3% from its own farm's effluent — near-complete farm-specific sourcing, matching the Stage F Bray-Curtis result (0.89, rank #1).
- **Cattle pair C2** was more mixed (20.9% cattle, 48.9% hospital, 30.2% unknown).
- The paired-vs-cross-compartment Wilcoxon test on ST2 proportions was non-significant (one-sided p = 0.844), identical in conclusion to the Stage F analysis (p = 0.84).

**4.8.3 Concordance between methods.** SourceTracker2 proportions correlated strongly with the Stage F descriptive metrics: Spearman ρ = 0.872 (p ≈ 0) vs Bray-Curtis similarity, ρ = 0.728 (p = 0.0009) vs Jaccard overlap, and ρ = 0.721 (p = 0.001) vs weighted shared fraction. The two approaches thus converge on the same biological conclusion: a shared *Acinetobacter*-rich environmental reservoir (best represented by cattle and hospital effluent) dominates worker hand communities, while poultry farm effluent — compositionally distinct (*Arcobacter*-rich) — is a poor source for poultry workers' hands.

## 5. Discussion

This comparative One Health survey delivers three main insights. **First**, sample type (effluent vs. worker hand-rinse) structures both the microbiome and the predicted resistome far more than the compartment of origin — a design-relevant result, since it means effluent and worker samples capture distinct, complementary facets of AMR-relevant communities and both should be retained in surveillance. **Second**, a 35-genus, *Acinetobacter*-dominated core spans poultry, cattle, and hospital compartments, and each farm sample shares 100–335 ASVs with hospital effluent. *Acinetobacter* is a priority nosocomial and environmental AMR genus; its ubiquity here is consistent with Bangladesh resistome-overlap studies [4, 7, 8] and with cross-sector One Health surveys elsewhere [6, 31, 34]. **Third**, both descriptive (shared-taxa) and formal (SourceTracker2 Bayesian) source analyses converge on the same conclusion: there is no uniform farm-specific environment→worker transmission. One cattle pair showed near-complete sourcing from its own effluent (ST2: 95.3%; Bray-Curtis: 0.89), whereas poultry workers' hands were sourced predominantly from hospital and cattle effluent (ST2: 15–87% hospital, 6–50% cattle) rather than from their own poultry farm effluent (ST2: 0.003–8.6%). The strong cross-method concordance (Spearman ρ = 0.872) increases confidence in this finding. This heterogeneity argues against a simple, deterministic farm→worker pathway and toward a shared environmental/water reservoir — enriched in *Acinetobacter* and spanning cattle and hospital compartments — that seeds multiple exposure routes. Directionality cannot be inferred from cross-sectional 16S data.

Relative to the prior Bangladesh poultry 16S study [1], this work adds the cattle and hospital comparators, paired worker hand-rinse sampling, and a curated predicted-resistome comparison — directly addressing the gaps in §1. It does not, however, reach the strain/ARG resolution of shotgun/MAG studies that can confirm transmission [15, 31].

## 6. Limitations

- **16S amplicon data cannot detect resistance genes, resolve strains, or infer horizontal gene transfer.** All resistome results are PICRUSt2 *predictions* of functional potential, cross-referenced to KEGG AMR classes — a proxy, not measurement.
- **Small, unbalanced sample** (n = 14; hospital n = 2 with no hand-rinse; only 2 cattle pairs), limiting statistical power; inferential tests are hypothesis-generating.
- **Cross-sectional** design precludes temporal or causal inference.
- **No phenotypic antimicrobial-susceptibility, MIC, or ARG-targeted molecular data** were available in the uploaded dataset, so the original antimicrobial-usage and phenotypic-resistance objectives could not be addressed directly.
- Reverse-read quality limited read retention (~20–42%), though sufficient depth remained for robust diversity estimates.

## 7. Conclusions and recommendations

Across poultry, cattle, and hospital compartments, worker-accessible and effluent microbiomes share a common, *Acinetobacter*-rich, AMR-relevant core, and community structure is organized chiefly by sample type. The data support a shared environmental reservoir model rather than uniform farm-specific worker acquisition. To convert these hypothesis-generating signals into confirmed transmission routes, we recommend: (1) **shotgun metagenomics** with ARG databases (CARD/ResFinder) and MAG/strain tracking on the same paired samples; (2) **culture-based antimicrobial-susceptibility testing** of indicator organisms (*E. coli*, *Enterococcus*, *Acinetobacter*); (3) a **larger, balanced, longitudinal** design with more cattle and hospital pairs and matched worker metadata; and (4) integration of antimicrobial-usage records to link practice to resistome.

---

## Figures (in `figures/`)
- **Fig 1** `fig1_study_design.png` — One Health study-design schematic.
- **Fig 2a/2b** `fig2a_phylum_composition.*`, `fig2b_genus_composition.*` — phylum/genus composition.
- **Fig 3** `fig3_alpha_diversity.*` — alpha diversity by site and sample type.
- **Fig 4** `fig4_pcoa.*` — PCoA (Bray–Curtis, weighted UniFrac).
- **Fig 5** `fig5_pathogen_genera_heatmap.*` — AMR-relevant genera heatmap.
- **Fig 6** `fig6_resistome_heatmap.*` — predicted-resistome class heatmap.
- **Fig 7** `fig7_source_tracking.*` — paired vs. cross-compartment source similarity.
- **Fig 7b** `fig7b_hospital_overlap.*` — hospital↔farm shared ASVs.
- **Fig 8** `fig8_sourcetracker2.*` — SourceTracker2 source proportions (stacked bar) + concordance with shared-taxa Bray-Curtis.

## Tables (in `tables/`)
1. `table1_sample_summary.csv` — per-sample metadata, diversity, NSTI.
2. `table2_alpha_kw.csv` — alpha-diversity Kruskal–Wallis.
3. `table3a/3b_permanova_*.csv` — taxonomic and resistome PERMANOVA.
4. `table4_differential_genera_aldex2.csv` — top differential genera.
5. `table5_pathogen_genera.csv` — AMR-relevant genera by group.
6. `table6_amr_classes.csv` — predicted resistome classes + tests.
7. `table7_core_genera.csv` — 35-genus cross-compartment core.
8. `table8_pair_sharing.csv` — paired source-sharing metrics.
9. `st2_source_summary.tsv` — SourceTracker2 per-worker source proportions.
   `st2_vs_shared_taxa.tsv` — SourceTracker2 vs shared-taxa merged table.
   `st2_correlation.tsv` — cross-method Spearman correlations.

## References
1. Yasmin et al. (2025). Metagenomic insights into microbial diversity and potential pathogenic transmission in poultry farm environments of Bangladesh. *BMC Microbiology*. doi:10.1186/s12866-025-03970-0
4. Flatgard et al. (2024). Tracking antimicrobial resistance transmission in urban and rural communities in Bangladesh. *Microbiology Spectrum*. doi:10.1128/spectrum.03956-23
5. Kador et al. (2026). Microbial diversity, functional genomics and antibiotic resistance in integrated chicken and fish farming systems of Bangladesh. *PLOS One*. doi:10.1371/journal.pone.0344367
6. Yang et al. (2025). Microbiome, resistome, and potential transfer of antibiotic resistance genes in Chinese wet market under One Health sectors. *BMC Microbiology*. doi:10.1186/s12866-025-04115-z
7. Swarthout et al. (2021). Differential overlap in human and animal fecal microbiomes and resistomes in rural versus urban Bangladesh. doi:10.1101/2021.05.13.21257188
8. Williams et al. (2023). Impact of contrasting poultry exposures on human, poultry, and wastewater antibiotic resistomes in Bangladesh. *Microbiology Spectrum*. doi:10.1128/spectrum.01763-23
13. Alam et al. (2019). Human exposure to antimicrobial resistance from poultry production: Assessing hygiene and waste-disposal practices in Bangladesh. *Int. J. Hyg. Environ. Health*. doi:10.1016/j.ijheh.2019.07.007
15. Scicchitano et al. (2024). Routes of dispersion of antibiotic resistance genes from the poultry farm system. *Sci. Total Environ.* doi:10.1016/j.scitotenv.2023.169086
31. Maciel-Guerra et al. (2022). Dissecting microbial communities and resistomes for interconnected humans, soil, and livestock. *ISME J.* doi:10.1038/s41396-022-01315-7
32. Randeni et al. (2026). Tracking Environmental Antimicrobial Resistance: E. coli across Hospital, Livestock, and Community Settings in Gampaha, Sri Lanka. doi:10.21203/rs.3.rs-10015644/v1
34. Kitano et al. (2026). Environmental Dissemination of Antimicrobial Resistance: A Resistome-Based Comparison of Hospital and Community Wastewater Sources. *Antibiotics*. doi:10.3390/antibiotics15010099
