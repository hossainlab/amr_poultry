# Study Plan: Cross-Compartment One Health Comparison of Microbial Communities and Predicted AMR Pathways Across Poultry Farms, Cattle Farms, and Hospital Effluent in Bangladesh

## 1. Summary

A cross-sectional, culture-independent 16S rRNA (V3–V4) amplicon survey comparing microbial community structure, diversity, and predicted antimicrobial-resistance functional pathways across three One Health compartments — poultry farm, cattle farm, and hospital — using paired effluent (waste) and farm-worker hand-rinse samples. The study tests whether (a) microbial communities and predicted AMR pathways differ by compartment and sample type, and (b) worker hand-rinse communities share taxa with the effluent of their own farm, indicating potential environmental-to-human transmission. AMR function is addressed via PICRUSt2 predicted KEGG pathways cross-referenced to structured resistome categories, with explicit predictive caveats. Deliverable: a publication-ready analysis with rigorous statistics and figures.

## 2. Data Available

- **Sequencing:** 14 samples, Illumina MiSeq paired-end 2×300, 16S V3–V4 (341F/806R primers still attached in reads). Read depth 62,909–109,456 reads/sample (~1.2M read pairs total).
- **Sample structure (from metadata.tsv):**
  - Poultry farm: PW1–PW4 (effluent, n=4) + PH1–PH4 (worker hand-rinse, n=4) — 4 paired effluent↔hand sets
  - Cattle farm: CW1–CW2 (effluent, n=2) + CH1–CH2 (worker hand-rinse, n=2) — 2 paired sets
  - Hospital: HW1–HW2 (effluent only, n=2) — no hand-rinse comparator
- **Metadata fields:** sample-id, sample-label, site, sample-type (Effluent / Workers hand rinse water), cohort (Farm / Farm-Workers / Hospital).
- **Not uploaded:** culture/API-20E, Kirby-Bauer/MIC, and ARG-PCR data described in the original objectives. The plan frames the study around the 16S data and notes phenotypic/ARG integration as a recommended extension if those tables become available.

## 3. Literature Review and Gap Analysis

### What exists
- **Bangladesh poultry 16S microbiome:** Yasmin et al. 2025 [1] profiled poultry farm environments (droppings, cloacal swabs, feed, hand swabs, soil, water) across three districts using 16S V3–V4 + QIIME2 + PICRUSt2, reporting Proteobacteria/Firmicutes dominance, pathogenic genera (Enterobacter, Acinetobacter, Shigella) enriched in hand swabs, and widespread predicted AMR pathways. Kador et al. 2026 [5] extended similar profiling to integrated chicken-fish systems. These establish that *single-compartment poultry 16S profiling in Bangladesh is no longer novel*.
- **Poultry→worker ARG transmission (high-resolution benchmark):** Scicchitano et al. 2024 [15] used shotgun metagenomics, MAG reconstruction, StrainPhlAn3 strain-level matching, and PathoFact across 281 samples (poultry gut, internal/external farm environment, worker gut/skin, cohabitants) in Italy, showing workers' microbiomes are the principal ARG dispersion route, with 180 poultry-derived species-level genome bins reaching workers and a core resistome partly on mobile elements. This is the methodological benchmark for transmission inference — and it explicitly requires shotgun depth that 16S cannot match.
- **Bangladesh behavioral/hygiene & culture-based transmission:** Alam et al. 2019 [13] assessed hygiene/waste-disposal practices and fecal contamination on poultry-worker hands in Bangladesh. Aworh et al. 2020 [18] (Nigeria) and Zhou et al. 2024 [19] (China) showed high ARG/carriage overlap between poultry and worker hand isolates via culture + PCR. Christodoulou 2023 [16] (Greece) and Oloyede 2019 [17] (Nigeria) reported shared resistance between poultry and worker E. coli/MRSA isolates.
- **Bangladesh resistome overlap (human vs animal):** Swarthout et al. 2021 [7] showed higher human–chicken gut microbiome and ARG-allele overlap in rural vs urban Bangladesh. Williams et al. 2023 [8] found wastewater carried the highest ARG richness, and occupational poultry exposure did not by itself shift human fecal resistomes — implicating the environment/wastewater as the key reservoir.
- **Cross-compartment / hospital comparators:** Flatgard et al. 2024 [4] tracked ESBL/carbapenem-resistant E. coli across urban/rural Bangladesh wastewater (households, wet markets). Kitano et al. 2026 [34] compared hospital vs community wastewater resistomes (Tokyo, high-income). Randeni et al. 2026 [32] (Sri Lanka) compared hospital/livestock/community E. coli susceptibility (culture-based). Yang et al. 2025 [6] profiled wet-market microbiome/resistome across humans, poultry, environment (China). Maciel-Guerra et al. 2022 [31] linked humans/soil/livestock resistomes on a single farm.
- **Reviews framing the environmental AMR reservoir:** Larsson & Flach 2021 [14] (Nature Rev Microbiol), He et al. 2020 [11], Chen et al. 2025 [12], Sassi et al. 2025 [30], Wojnarowski et al. 2025 [28].

### Identified gaps this study can fill
1. **No Bangladesh study simultaneously compares poultry, cattle, AND hospital effluent microbiomes with paired worker hand-rinse samples under one 16S design.** Existing Bangladesh work is poultry-only [1, 5] or single-pathogen culture-based [4, 13]. The three-compartment design lets us position farm effluent against a clinical (hospital) reservoir — a comparison only available elsewhere as culture-based [32] or in high-income settings [34].
2. **Paired effluent↔hand-rinse whole-community profiling is rare in LMIC One Health.** Most poultry→worker transmission evidence in Bangladesh/LMICs is culture-based single-pathogen (E. coli, MRSA) [13, 16, 17, 18, 19]. A culture-independent, whole-community source-tracking of paired samples is a complementary, broader lens.
3. **Cross-compartment predicted-resistome comparison is missing for Bangladesh.** Yasmin 2025 [1] predicted AMR pathways via PICRUSt2 but only within poultry. Comparing predicted AMR functional profiles across poultry/cattle/hospital effluent and worker hands has not been done in this setting.
4. **Cattle as a livestock comparator to poultry** is under-represented in Bangladesh AMR microbiome work, which is overwhelmingly poultry-focused.

### Limitations to frame honestly (informed by literature)
- 16S cannot detect ARGs directly, resolve strains, or infer horizontal gene transfer — only predict functional *potential* [1, 15]. PICRUSt2 predictions depend on reference genomes and are putative [1].
- The shotgun/MAG/strain-matching resolution of Scicchitano 2024 [15] is not achievable with 16S; transmission claims are therefore community-level and inferential, not strain-confirmed.
- Small, unbalanced sample (n=14; hospital has no hand-rinse and only n=2 effluent; cattle n=2 pairs). Statistical power is limited; results are hypothesis-generating.
- Cross-sectional design captures no temporal/longitudinal dynamics [15, 25].
- No phenotypic AST/MIC or ARG-PCR integration in the uploaded data; predicted AMR cannot be validated against observed resistance phenotypes.

## 4. Refined Study Framing (Comparative One Health)

**Study type:** Cross-sectional, comparative, culture-independent 16S rRNA amplicon survey with predictive functional/resistome profiling across three One Health compartments.

**Refined title (working):** "Cross-compartment comparison of microbial communities and predicted antimicrobial-resistance pathways across poultry farms, cattle farms, and hospital effluent in Bangladesh: a One Health 16S rRNA amplicon study"

**Refined objectives (mapped to feasible analyses on the uploaded data):**
1. Characterize and compare taxonomic composition and diversity (alpha + beta) of microbial communities in effluent and worker hand-rinse samples across poultry, cattle, and hospital compartments.
2. Identify differentially abundant taxa and compartment-enriched pathogenic/resistance-associated genera across compartments and sample types.
3. Predict metabolic and AMR-related functional pathways within each community using PICRUSt2, and compare predicted resistome category profiles across compartments.
4. Evaluate shared microbial taxa between paired farm effluent and worker hand-rinse samples (poultry n=4, cattle n=2) using community-level source tracking and shared-core analysis to infer potential environmental-to-human transmission.
5. Position hospital effluent as a clinical-reservoir comparator against farm effluent to contextualize farm-to-clinical AMR overlap.

**Original objectives 1–3 (culture/API-20E, AST/MIC, ARG-PCR) are retained as a recommended integrative extension** if those data tables become available; they are not part of the current 16S-only analysis.

## 5. Analysis Pipeline

### Stage A — QC and preprocessing
- FastQC + MultiQC on raw FASTQ (per-sample quality profiles, adapter check).
- Primer removal with cutadapt (341F: `CCTACGGGNGGCWGCAG`, 806R: `GACTACHVGGGTATCTAATCC`); discard untrimmed reads (require both primers).
- Import demultiplexed paired-end FASTQ into QIIME2 as a `CasavaOneEightSingleLanePerSampleDirFmt` artifact.

### Stage B — ASV inference (DADA2 via QIIME2)
- `dada2 denoise-paired`: after primer trimming, set `trunc-len-f 0`, `trunc-len-r 0` (V3–V4 reads are ~260 bp post-primer with quality retained to ~290), `max-ee-f 2`, `max-ee-r 2`, `trunc-q 2`, `min-overlap 12`, `n-threads` to machine core count. Justify: V3–V4 amplicon ~460 bp with 2×300 gives adequate overlap after primer removal; no fixed truncation avoids unnecessary read loss at this moderate depth.
- Generate ASV table (feature table), representative sequences, and track read retention per sample (flag any sample <10k reads post-DADA2).
- Taxonomy: classify-sklearn against **SILVA 138.2** (99% OTU/full-length 16S classifier) as primary; optionally cross-check with Greengenes2 2022.10 for consistency with [1]. Filter chloroplast/mitochondria/archaea as appropriate for the bacterial-community question.

### Stage C — Diversity
- Rarefy to the minimum retained sample depth for alpha diversity only (observed features, Shannon, Pielou's evenness, Faith's phylogenetic PD); build rooted phylogeny via `align-to-tree-mafft-iqtree`.
- Beta diversity: Bray–Curtis, weighted UniFrac, unweighted UniFrac. Ordination via PCoA (and NMDS for Bray–Curtis as a non-parametric cross-check).
- Group tests: PERMANOVA (9999 permutations, strata by farm pair where applicable) on `site` (poultry/cattle/hospital), `sample-type` (effluent/hand-rinse), and `site × sample-type`; report R² and pseudo-F. Pairwise PERMANOVA with BH-FDR. Test dispersion homogeneity (PERMDISP/betadisper) and report it alongside PERMANOVA.
- Alpha diversity group comparisons: Kruskal–Wallis + Dunn's post-hoc with BH-FDR; report effect sizes (epsilon-squared).

### Stage D — Differential abundance & pathogen-risk taxa
- Differential abundance across compartments/sample-types with **ANCOM-BC** (bias-corrected log-fold change, controls compositionality) at genus level; supplement with prevalence-based core-microbiome analysis.
- Flag and tabulate known pathogenic / resistance-associated genera (Enterobacter, Escherichia/Shigella, Acinetobacter, Pseudomonas, Staphylococcus, Enterococcus, Klebsiella, Salmonella, Campylobacter) per compartment as a proxy AMR-risk profile (clearly labeled as taxonomic presence, not confirmed virulence/resistance).

### Stage E — Functional & resistome prediction (PICRUSt2)
- Run PICRUSt2 (place_features → hsp.py for predicted 16S → metagenome_pipeline) on the ASV table to infer KEGG Orthology (KO) abundances and pathway abundances per sample.
- Extract AMR-related KEGG pathways/genes (beta-lactam, aminoglycoside, macrolide, tetracycline, fluoroquinolone, sulfonamide, glycopeptide, polymyxin, multidrug efflux, 23S rRNA methyltransferase, etc.) using the same category set as [1] for comparability.
- **Resistome DB cross-reference:** map predicted AMR KO/enzyme categories to structured resistome classes (CARD ontology categories: beta-lactam resistance, aminoglycoside resistance, MLS, tetracycline, phenicol, sulfonamide, fluoroquinolone, glycopeptide, polymyxin, multidrug) to produce a compartment × resistome-class abundance matrix. Flag all results as *predicted functional potential*, not detected ARGs.
- Compare predicted AMR pathway/resistome profiles across compartments (PERMANOVA on functional Bray–Curtis; Kruskal–Wallis per class with BH-FDR).

### Stage F — Transmission / shared-taxa inference (paired design)
- **Shared-core analysis:** identify ASVs/genera present in both members of each paired effluent↔hand-rinse set (poultry n=4, cattle n=2); report shared vs unique taxa per pair and across pairs (Venn/upset).
- **Source tracking:** run SourceTracker2 (or FEAST) with effluent as source community and the matched worker hand-rinse as sink, per farm pair, to estimate the proportion of the hand-rinse community attributable to effluent vs unknown/other sources. Report per-pair source proportions with bootstrap CIs.
- **Cross-compartment overlap:** compute shared genera between hospital effluent and farm effluent to quantify farm↔clinical environmental overlap.
- Frame all transmission results as community-level inferential evidence of *potential* exposure/overlap, not strain-confirmed transmission (per [15] limitation).

### Stage G — Figures and tables (publication-ready)
All figures: colorblind-friendly palette, Liberation Sans font, saved as both .svg (editable text) and .png; media-output-checked after generation.
1. Study design schematic (compartments, sample types, pairing) — conceptual figure via GenerateImage.
2. Read-retention / QC summary (MultiQC-style) — data figure.
3. Stacked bar plots of relative abundance at phylum and genus level by compartment × sample-type.
4. Alpha diversity boxplots (4 metrics) by site and sample-type with significance annotations.
5. PCoA ordination (Bray–Curtis, weighted/unweighted UniFrac) colored by site, shaped by sample-type, with PERMANOVA R² in legend.
6. Heatmap of top differentially abundant genera across compartments (ANCOM-BC results).
7. Heatmap of predicted AMR/resistome-class abundances across compartments.
8. Source-tracking stacked bar (proportion of hand-rinse community from effluent per pair) + UpSet/Venn of shared taxa.
9. Pathogen-risk genera summary table (presence/relative abundance by compartment).

Tables: T1 sample metadata + read stats; T2 alpha diversity stats; T3 PERMANOVA + PERMDISP; T4 ANCOM-BC differential taxa; T5 predicted resistome-class comparison; T6 shared-taxa/source-tracking per pair.

## 6. Statistical Rigor and Assumptions
- Multiple testing: BH-FDR throughout; significance α=0.05 for both p and q.
- Effect sizes reported alongside p-values (PERMANOVA R², Kruskal–Wallis ε², ANCOM-BC log-fold change).
- Compositionality addressed via ANCOM-BC (not raw relative-abundance tests) for differential abundance.
- PERMDISP reported with every PERMANOVA to disentangle location vs dispersion effects.
- Rarefaction used only for alpha diversity and phylogenetic metrics; beta/diversity and DA use un rarefied counts with appropriate methods.
- Small-sample caveat stated explicitly; hospital (n=2, no hand-rinse) treated as a comparator only, not for within-hospital statistical inference.
- All PICRUSt2/resistome results labeled "predicted functional potential."
- NSTI (nearest sequenced taxon index) reported per sample to qualify PICRUSt2 prediction confidence.

## 7. Compute / Resource Estimate
- **Input:** 14 paired samples, ~1.2M read pairs total, ~530 MB compressed.
- **Workload classification:** light 16S amplicon denoising + PICRUSt2 + R downstream. DADA2 on ~1.2M reads runs in minutes; PICRUSt2 is the heaviest step (~30–60 min at this scale); R stats/figures minutes.
- **Resources:** fits on a single right-sized sandbox machine (8 CPU / 16 GB RAM is ample; <8 GB resident memory, <5 GB working disk). No HPC tools required.
- **Runtime estimate:** ~1.5–3 h end-to-end including QC, DADA2, diversity, PICRUSt2, source-tracking, and figure generation.
- **Execution target:** default/worker machine via NotebookEdit; chunk into Stage A–G cells with checkpoints to /workspace and final figures/tables to /mnt/results.

## 8. Assumptions
- Only the 14 uploaded 16S samples are in scope; culture/AST/ARG-PCR data are out of scope unless later provided.
- SILVA 138.2 is the primary taxonomy reference; Greengenes2 used only as a cross-check.
- "Effluent" = poultry/cattle farm waste effluent; "Workers hand rinse water" = farm-worker hand-rinse; hospital samples are effluent only.
- Poultry is the primary compartment of interest; cattle and hospital are comparators (per comparative One Health framing).
- Predicted AMR pathways are functional-potential inference, not ARG detection — all claims worded accordingly.
- Sample size is hypothesis-generating; no causal transmission claims, only community-level overlap/source-attribution.

## 9. Recommended Future Extensions (out of current scope)
- Integrate culture/API-20E + AST/MIC + ARG-PCR tables (original objectives 1–3) to validate predicted AMR against observed phenotypic/genotypic resistance.
- Shotgun metagenomics on a subset to enable MAG/strain-level transmission confirmation and direct ARG/MGE detection, following the Scicchitano 2024 [15] design.
- Longitudinal sampling across rearing cycles to capture temporal dynamics [15, 25].
- Expand hospital and cattle sample sizes and add hospital-worker hand-rinse for a fully balanced three-compartment paired design.
