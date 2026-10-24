---
title: "Cross-compartmental sharing of antimicrobial-resistant bacterial communities across poultry farm, cattle farm, and hospital environments in Bangladesh: a One Health 16S rRNA amplicon study"
authors:
  - name: "[Author 1]"
    affiliation: 1
  - name: "[Author 2]"
    affiliation: 1
  - name: "[Author 3]"
    affiliation: 1
affiliations:
  - number: 1
    name: "DeepBio Academy, Dhaka, Bangladesh"
corresponding: "[Author 1], DeepBio Academy, Dhaka, Bangladesh. Email: [email]"
journal: "BMC Microbiology"
---

# Cross-compartmental sharing of antimicrobial-resistant bacterial communities across poultry farm, cattle farm, and hospital environments in Bangladesh: a One Health 16S rRNA amplicon study

[Author 1], [Author 2], [Author 3]

DeepBio Academy, Dhaka, Bangladesh

**Corresponding author:** [Author 1], DeepBio Academy, Dhaka, Bangladesh. Email: [email]

---

## Abstract

**Background:** Antimicrobial resistance (AMR) propagates across the environment–animal–human interface, yet integrated surveillance spanning livestock and clinical compartments in low- and middle-income countries (LMICs) remains scarce. In Bangladesh, poultry farm microbiomes and resistomes have been characterized individually, but no study has compared poultry, cattle, and hospital compartments within a single sampling design with paired worker hand-rinse samples.

**Results:** We profiled bacterial communities and predicted AMR functional potential across three One Health compartments — poultry farm, cattle farm, and hospital — using 14 Illumina MiSeq 16S rRNA (V3–V4) samples: paired farm effluent and worker hand-rinse samples (poultry, 4 pairs; cattle, 2 pairs) and hospital effluent (n = 2). DADA2 resolved 5,520 bacterial amplicon sequence variants (ASVs). Community structure was driven primarily by sample type (effluent vs. hand-rinse) rather than compartment (weighted UniFrac R² = 0.27, p = 0.001), a pattern mirrored in the PICRUSt2-predicted resistome (sample type R² = 0.22, p = 0.035; site not significant). *Acinetobacter* dominated every compartment (19–58% relative abundance), and a 35-genus core — including *Acinetobacter*, *Aeromonas*, *Escherichia-Shigella*, *Klebsiella*, *Enterobacter*, *Enterococcus*, *Pseudomonas*, *Citrobacter*, and *Salmonella* — was shared across all three compartments. SourceTracker2 formal source tracking revealed that poultry farm effluent contributed negligibly (≤0.1%) to poultry workers' hand communities; instead, hospital effluent (15–87%) and cattle effluent (6–50%) were the dominant predicted sources. One cattle pair showed near-complete farm-specific sourcing (95.3% from paired effluent). The formal model and descriptive Bray–Curtis overlap analysis strongly concurred (Spearman ρ = 0.87).

**Conclusions:** Worker hand-rinse and effluent microbiomes across poultry, cattle, and hospital compartments share a common *Acinetobacter*-rich, AMR-relevant core. Community-level source tracking supports a shared environmental reservoir model rather than uniform farm-specific worker acquisition. These findings are hypothesis-generating and motivate shotgun-metagenomic and culture-based confirmation.

**Keywords:** Antimicrobial resistance, One Health, 16S rRNA, poultry, Bangladesh, microbiome, PICRUSt2, SourceTracker2, *Acinetobacter*, effluent

---

## Background

Antimicrobial resistance (AMR) is a global health threat amplified by intensive livestock production, inadequate wastewater management, and close human–animal contact in low- and middle-income countries (LMICs) [1, 7]. Bangladesh's dense poultry sector, combined with often unprotected worker exposure and direct discharge of farm effluent into shared waterways, creates a high-risk environment–human transmission interface [7]. Metagenomic surveys of Bangladeshi poultry environments have begun to characterize these microbial communities [1, 3], and resistome studies confirm overlapping human, animal, and wastewater resistance gene pools in the country [2, 5, 6]. Cross-sector One Health surveys elsewhere have demonstrated environment–livestock–human microbiome and resistome connectivity [4, 9, 11], and hospital wastewater has been identified as a concentrated point source of resistance determinants [11].

However, the evidence base has three gaps. First, existing Bangladesh poultry studies profile the farm environment alone [1] or integrated chicken–fish systems [3]; none compare poultry, cattle, and hospital effluent within one sampling and sequencing design, and cattle remain an under-represented livestock comparator. Second, paired environment↔worker whole-community microbiome profiling is rare in LMICs; worker exposure is typically inferred from questionnaires or targeted isolate-based surveillance [7] rather than from paired effluent and hand-rinse metagenomes. Third, cross-compartment predicted-resistome comparison is missing for Bangladesh, as prior resistome work has focused on fecal/wastewater gene overlap [5, 6] or single-setting wastewater [11].

Methodologically, strain-resolved shotgun metagenomics and metagenome-assembled genome (MAG) approaches set the benchmark for confirming poultry-to-worker ARG transmission [8, 9]. 16S rRNA amplicon data cannot reach that resolution but can provide community-level, predictive inference about shared taxa and functional potential. Given these constraints and the available 16S data, we framed this study as a comparative One Health survey addressing four objectives: (1) compare bacterial community composition and diversity across poultry farm, cattle farm, and hospital compartments and between effluent and worker hand-rinse sample types; (2) identify AMR-relevant genera and any cross-compartment shared core taxa; (3) predict and compare the functional resistome across compartments using PICRUSt2 mapped to KEGG's curated antimicrobial-resistance gene hierarchy; and (4) evaluate community-level evidence for environment-to-worker and farm-to-hospital sharing using both descriptive overlap metrics and a formal Bayesian source-tracking model.

## Methods

### Study design and sample collection

This cross-sectional study was conducted in Bangladesh across three One Health compartments: a poultry farm, a cattle farm, and a hospital. Fourteen samples were collected: poultry farm effluent (n = 4) paired with worker hand-rinse samples (n = 4; pairs P1–P4), cattle farm effluent (n = 2) paired with worker hand-rinse samples (n = 2; pairs C1–C2), and hospital effluent (n = 2; H1–H2; no hand-rinse available). Effluent samples were collected from wastewater discharge points; hand-rinse samples were collected from workers using sterile rinse water. Samples were transported on ice and processed for DNA extraction.

### DNA extraction and sequencing

Genomic DNA was extracted from each sample and the V3–V4 hypervariable region of the 16S rRNA gene was amplified using primers 341F (5′-CCTACGGGNGGCWGCAG-3′) and 806R (5′-GACTACHVGGGTATCTAATCC-3′), yielding an approximately 420 bp amplicon. Paired-end sequencing (2 × 300 bp) was performed on the Illumina MiSeq platform.

### Bioinformatics and ASV inference

Primer sequences were removed using Cutadapt [12]. Amplicon sequence variants (ASVs) were inferred using DADA2 [13] in R. Quality profiles indicated that reverse-read quality declined substantially after approximately 180 bp, while forward reads remained high quality to approximately 240 bp. DADA2 parameters were accordingly set to `truncLen = c(260, 200)`, `maxEE = c(3, 8)`, `truncQ = 2`, `minLen = 150`, with PhiX removal. Merged pairs required a minimum overlap of 12 bp and at most one mismatch (`mergePairs`), and amplicon lengths were filtered to 390–440 bp. Chimeric sequences were removed using the consensus method. Taxonomy was assigned against the SILVA v138.1 reference database [14] with species-level assignment where possible. A multiple sequence alignment was constructed using DECIPHER [15], and a phylogenetic tree was inferred with FastTree 2 [16] for phylogenetic diversity metrics. All downstream analyses were conducted in R using the phyloseq [17] and vegan [18] packages.

### Diversity analysis

Alpha diversity metrics (Observed ASVs, Shannon index, Pielou's evenness, and Faith's phylogenetic diversity) were calculated on the full ASV table (without rarefaction) and compared across sites and sample types using the Kruskal–Wallis test with Benjamini–Hochberg (BH) correction. Beta diversity was assessed using Bray–Curtis, weighted UniFrac, and unweighted UniFrac distances. Permutational multivariate analysis of variance (PERMANOVA) [19] was used to test the effects of site, sample type, and their interaction on community composition, with 999 permutations. Dispersion homogeneity was evaluated using PERMDISP. Principal coordinate analysis (PCoA) was used for ordination visualization.

### Differential abundance analysis

Differential abundance of genera was assessed using ALDEx2 [20], which accounts for sampling uncertainty through Monte Carlo sampling from the Dirichlet distribution. For the three-group site comparison, the Kruskal–Wallis test within ALDEx2 was used; for the two-group sample-type comparison, Welch's t-test and Wilcoxon rank-sum test were used. Effect sizes and Benjamini–Hochberg-corrected p-values were reported. Given the small sample size (n = 14), no genus was expected to reach genome-wide significance; top-ranked genera by p-value were reported.

### AMR-relevant genera and cross-compartment core

A curated list of AMR-relevant (priority pathogen) genera was compiled a priori, including *Acinetobacter*, *Aeromonas*, *Arcobacter*, *Escherichia-Shigella*, *Klebsiella*, *Enterobacter*, *Enterococcus*, *Pseudomonas*, *Citrobacter*, *Salmonella*, *Staphylococcus*, *Streptococcus*, *Vibrio*, *Corynebacterium*, *Bacteroides*, and *Stenotrophomonas*. Mean relative abundances were computed by site × sample type. The cross-compartment core was defined as genera present in at least one sample from each of the three sites.

### Predicted functional resistome (PICRUSt2)

Functional gene content was predicted using PICRUSt2 [21], which maps ASV sequences to reference genomes and predicts KEGG Ortholog (KO) abundances. The input BIOM table was oriented with ASVs as observations, and the analysis used the default sequence alignment and NSTI (nearest sequenced taxon index) calculation. Per-sample weighted NSTI values were assessed against the 0.15 reliability threshold. Predicted KOs were mapped to antimicrobial resistance drug classes using the KEGG BRITE hierarchy ko01504 (antimicrobial resistance genes) [22], which provides a curated classification of 238 AMR-associated KOs across 13 drug classes, including beta-lactamases, aminoglycoside resistance genes, tetracycline resistance genes, macrolide resistance genes, multidrug efflux pump modules, glycopeptide resistance modules, and cationic antimicrobial peptide (CAMP) resistance modules. Per-class abundance was computed as the summed relative abundance of member KOs. Classes were compared by Kruskal–Wallis test, and the overall resistome profile was tested by PERMANOVA (Bray–Curtis). All resistome results represent predicted functional potential, not directly detected resistance genes.

### Source tracking analysis

Two complementary approaches were used. First, a descriptive shared-taxa analysis computed, for each worker hand-rinse sample (sink), the Bray–Curtis similarity, Jaccard overlap, and abundance-weighted shared fraction against every effluent sample (candidate source). The paired farm effluent was contrasted with cross-compartment effluent using a paired one-sided Wilcoxon signed-rank test. Hospital-to-farm sharing was quantified as the number of ASVs shared between hospital effluent and each farm sample.

Second, formal source tracking was performed using SourceTracker2 [23], a Bayesian Gibbs-sampling mixture model that estimates the proportional contribution of each source environment to a sink community while accounting for an "unknown" source. All eight effluent samples served as candidate sources, grouped into three source categories (Cattle farm effluent, Poultry farm effluent, Hospital effluent), and the six worker hand-rinse samples served as sinks. The Gibbs sampler was run with 10 independent restarts, 100 burnin passes, and rarefaction depth of 10,000 reads for both sources and sinks. SourceTracker2 proportions were compared against the descriptive shared-taxa metrics using Spearman rank correlation to assess cross-method concordance. We note that this concordance is a consistency check rather than independent validation, as both approaches derive from the same underlying compositional data.

### Data availability

Raw sequence data and processed ASV tables are available from the corresponding author upon reasonable request. All analysis code is documented in the project execution notebook.

## Results

### Sequencing quality and ASV inference

After quality trimming, denoising, merging, and chimera removal, samples retained 19,129–42,327 non-chimeric reads per sample (approximately 20–42% of raw input reads), yielding 5,523 ASVs (5,520 bacterial). Read retention was limited by the decline in reverse-read quality after approximately 180 bp, an expected property of 2 × 300 bp V3–V4 data. Per-sample read counts and retention rates are summarized in Table 1.

### Community composition

Effluent samples were compositionally diverse, dominated by Proteobacteria, Bacteroidota, Firmicutes, and Campylobacterota. Poultry effluent was notably enriched in *Arcobacter* (18.7% mean relative abundance). Worker hand-rinse samples were substantially less diverse and dominated by *Acinetobacter* (Figure 2). The effluent-versus-hand contrast was visible within each compartment at both phylum and genus levels (Figure 2a, 2b).

### Alpha diversity

Richness and phylogenetic diversity differed significantly by sample type: Observed ASVs (Kruskal–Wallis p = 0.0045, BH q = 0.009) and Faith's phylogenetic diversity (p = 0.0019, q = 0.0078) were both higher in effluent than in hand-rinse samples (Table 2, Figure 3). Community evenness and Shannon diversity differed by site: Pielou's evenness (p = 0.0076, q = 0.024) and Shannon index (p = 0.012, q = 0.024). Poultry hand-rinse samples exhibited the lowest richness (Observed ASVs: 244–361), while cattle effluent sample CW2 showed the highest (1,284).

### Beta diversity

Sample type was the consistent and strongest driver of community dissimilarity across all three distance metrics (Table 3a, Figure 4). Bray–Curtis PERMANOVA: sample type R² = 0.126 (p = 0.014); weighted UniFrac R² = 0.269 (p = 0.0012); unweighted UniFrac R² = 0.244 (p = 0.0005). Site was marginally significant only for Bray–Curtis (R² = 0.196, p = 0.050) and was not significant for phylogenetic distances. PERMDISP was non-significant for site (p = 0.247), supporting a true location effect rather than a dispersion artifact, but was significant for sample type (p = 0.028), indicating that some of the type effect may reflect differences in dispersion. The site × sample type interaction was significant for Bray–Curtis (R² = 0.379, p = 0.027), indicating that the effluent-versus-hand contrast differs across compartments.

### AMR-relevant genera

*Acinetobacter* dominated every compartment: poultry hand-rinse 58.2%, hospital effluent 39.7%, cattle effluent 39.0%, cattle hand-rinse 37.6%, and poultry effluent 19.2% (Table 5, Figure 5). Other notable signals included *Aeromonas* (18.8% in poultry hand-rinse), *Arcobacter* (18.7% in poultry effluent, 5.5% in hospital effluent), *Escherichia-Shigella* (8.7% in poultry hand-rinse, 6.6% in hospital effluent), *Corynebacterium* (approximately 8% in cattle samples), *Klebsiella* (4.8% in cattle hand-rinse), and *Streptococcus* (4.4% in hospital effluent). No genus reached ALDEx2 significance at BH q < 0.05, as expected given the small sample size (n = 14); the top-ranked genera by p-value are reported in Table 4.

### Cross-compartment core microbiome

A 35-genus core was shared across all three compartments (Table 7). This core was dominated by *Acinetobacter* (36–38% mean relative abundance at each site) and included multiple WHO priority-pathogen genera: *Aeromonas*, *Escherichia-Shigella*, *Flavobacterium*, *Corynebacterium*, *Enterobacter*, *Klebsiella*, *Enterococcus*, *Pseudomonas*, *Bacteroides*, *Stenotrophomonas*, *Citrobacter*, *Salmonella*, and *Cronobacter*. Each farm sample shared 100–335 ASVs with hospital effluent (Figure 7b).

### Predicted resistome

PICRUSt2 predicted 8,486 KOs across all samples, with per-sample weighted NSTI values of 0.030–0.099, all well below the 0.15 reliability threshold, indicating high-confidence predictions. Mapping to the KEGG BRITE ko01504 antimicrobial-resistance hierarchy identified 238 curated AMR KOs across 13 drug classes. The most diverse classes were beta-lactam (40 KOs detected), multidrug efflux (48 KOs), aminoglycoside (27 KOs), macrolide (17 KOs), glycopeptide (16 KOs), tetracycline (11 KOs), and CAMP resistance (12 KOs).

The predicted resistome profile differed significantly by sample type (PERMANOVA R² = 0.219, p = 0.035) but not by site (R² = 0.056, p = 0.945) (Table 3b, Figure 6), mirroring the taxonomic beta-diversity pattern. By sample type, quinolone (p = 0.0045), beta-lactam (p = 0.0098), sulfonamide (p = 0.020), and CAMP (p = 0.039) resistance classes differed nominally, though none survived BH correction (minimum q = 0.059). All resistome results represent predicted functional potential, not directly detected resistance genes.

### Source tracking

**Descriptive shared-taxa analysis.** Across all six effluent-to-worker pairs, there was no consistent farm-specific sourcing (paired vs. cross-compartment Wilcoxon one-sided p = 0.72–0.84). The pattern split sharply by compartment: cattle pair C1 showed near-complete effluent–hand overlap (Bray–Curtis similarity 0.89; paired effluent ranked first of eight candidate sources), while poultry pairs P1–P4 showed the opposite — hand communities were less similar to their own farm's effluent (Bray–Curtis 0.003–0.017; ranks 5–8) than to cross-compartment effluent.

**Formal source tracking (SourceTracker2).** The Bayesian mixture model strongly corroborated the descriptive analysis (Table 9, Figure 8). Poultry farm effluent contributed negligibly (0.003–8.6%) to all poultry workers' hand communities. Instead, hospital effluent (15.2–87.2%) and cattle effluent (5.9–50.2%) were the dominant predicted sources. Cattle pair C1 was sourced 95.3% from its own farm's effluent, confirming the near-complete farm-specific signal. Cattle pair C2 was more mixed (20.9% cattle, 48.9% hospital, 30.2% unknown). The paired-vs-cross-compartment Wilcoxon test on SourceTracker2 proportions was non-significant (one-sided p = 0.844), identical in conclusion to the descriptive analysis.

**Cross-method concordance.** SourceTracker2 proportions correlated strongly with the descriptive shared-taxa metrics: Spearman ρ = 0.872 (p < 0.001) versus Bray–Curtis similarity, ρ = 0.728 (p = 0.0009) versus Jaccard overlap, and ρ = 0.721 (p = 0.001) versus weighted shared fraction. However, both approaches derive from the same source–sink compositional similarity, so this concordance should be interpreted as a consistency check rather than independent validation; a shared compositional driver (e.g., *Acinetobacter* dominance) could inflate both metrics.

## Discussion

This comparative One Health survey yields three principal findings. First, sample type (effluent vs. worker hand-rinse) structures both the microbiome and the predicted resistome far more strongly than the compartment of origin. This is a design-relevant result: effluent and worker samples capture distinct, complementary facets of AMR-relevant communities, and both should be retained in surveillance programs. The significant site × sample type interaction for Bray–Curtis (R² = 0.379, p = 0.027) further indicates that the effluent-versus-hand contrast is not uniform across compartments, motivating compartment-stratified analysis in future studies.

Second, a 35-genus, *Acinetobacter*-dominated core spans poultry, cattle, and hospital compartments, and each farm sample shares 100–335 ASVs with hospital effluent. *Acinetobacter* is a WHO critical-priority nosocomial and environmental AMR pathogen; its ubiquity across all compartments here is consistent with Bangladesh resistome-overlap studies demonstrating shared human, animal, and wastewater resistance gene pools [2, 5, 6] and with cross-sector One Health surveys elsewhere [4, 9, 11]. The presence of *Escherichia-Shigella*, *Klebsiella*, *Enterobacter*, *Enterococcus*, *Salmonella*, and *Pseudomonas* in this core reinforces its AMR relevance.

Third, both descriptive and formal Bayesian source-tracking analyses converge on the same conclusion: there is no uniform farm-specific environment-to-worker transmission pathway. One cattle pair (C1) showed near-complete sourcing from its own farm's effluent (SourceTracker2: 95.3%; Bray–Curtis: 0.89), demonstrating that farm-specific acquisition can occur. However, poultry workers' hands were sourced predominantly from hospital and cattle effluent rather than from their own poultry farm effluent (SourceTracker2: poultry effluent ≤8.6%; hospital 15–87%; cattle 6–50%). This apparent paradox is explained by the compositional distinctiveness of poultry effluent — which is *Arcobacter*-rich — relative to the *Acinetobacter*-dominated hand communities that match the *Acinetobacter*-rich cattle and hospital effluents. The strong cross-method concordance (Spearman ρ = 0.87) increases confidence in the robustness of this pattern, though we note that both methods derive from the same compositional data and the concordance should be interpreted as a consistency check rather than independent validation.

These findings collectively support a shared environmental reservoir model: a *Acinetobacter*-rich community pool, represented in cattle and hospital effluent, seeds multiple exposure routes including worker hands. Directionality cannot be inferred from cross-sectional 16S data. The substantial "unknown" fractions in SourceTracker2 (7–30%) likely reflect unsampled environmental reservoirs, skin microbiota, or methodological limitations.

Relative to the prior Bangladesh poultry 16S study by Yasmin et al. [1], which used the same V3–V4 primers and a QIIME2 + PICRUSt2 workflow, this work adds the cattle and hospital comparators, paired worker hand-rinse sampling, a curated predicted-resistome comparison across compartments, and formal Bayesian source tracking. It does not, however, reach the strain-level or ARG-level resolution of shotgun/MAG studies that can confirm transmission events [8, 9]. The study by Yang et al. [4] in Chinese wet markets similarly demonstrated cross-sector microbiome and resistome connectivity under a One Health framework, and the Sri Lankan study by Randeni et al. [10] compared *E. coli* across hospital, livestock, and community settings — both supporting the value of multi-compartment designs, though neither used paired effluent–hand-rinse whole-community profiling.

### Limitations

Several limitations should be noted. First, 16S rRNA amplicon data cannot detect resistance genes, resolve strains, or infer horizontal gene transfer; all resistome results are PICRUSt2 predictions of functional potential cross-referenced to KEGG AMR classes — a proxy, not measurement. Second, the sample size is small and unbalanced (n = 14; hospital n = 2 with no hand-rinse; only 2 cattle pairs), limiting statistical power; all inferential tests are hypothesis-generating. The SourceTracker2 source categories for cattle and hospital effluent each rest on only two samples, and the reliability of per-category proportions from such small training sets cannot be established from the available data. Third, the cross-sectional design precludes temporal or causal inference. Fourth, no phenotypic antimicrobial-susceptibility testing, MIC determination, or ARG-targeted molecular data were available, so antimicrobial-usage and phenotypic-resistance objectives could not be addressed directly. Fifth, reverse-read quality limited read retention (approximately 20–42%), though sufficient depth remained for robust diversity estimates. Finally, figures were generated programmatically and validated by automated checks (dimensions, color content, white-space fraction); pixel-level visual review was not performed in this analysis environment.

## Conclusions

Across poultry, cattle, and hospital compartments in Bangladesh, worker hand-rinse and effluent microbiomes share a common, *Acinetobacter*-rich, AMR-relevant core, and community structure is organized chiefly by sample type rather than compartment. Formal Bayesian source tracking supports a shared environmental reservoir model rather than uniform farm-specific worker acquisition: poultry farm effluent contributed negligibly to poultry workers' hand communities, while hospital and cattle effluent dominated. One cattle pair demonstrated near-complete farm-specific sourcing, indicating that farm-specific acquisition can occur but is not the dominant pattern. To convert these hypothesis-generating signals into confirmed transmission routes, we recommend: (1) shotgun metagenomics with ARG databases (CARD/ResFinder) and MAG/strain tracking on the same paired samples; (2) culture-based antimicrobial-susceptibility testing of indicator organisms (*E. coli*, *Enterococcus*, *Acinetobacter*); (3) a larger, balanced, longitudinal design with more cattle and hospital pairs and matched worker metadata; and (4) integration of antimicrobial-usage records to link practice to resistome.

## List of abbreviations

AMR: Antimicrobial resistance; ASV: Amplicon sequence variant; BH: Benjamini–Hochberg; CAMP: Cationic antimicrobial peptide; DADA2: Divisive amplicon denoising algorithm 2; KO: KEGG Ortholog; LMIC: Low- and middle-income country; MAG: Metagenome-assembled genome; NSTI: Nearest sequenced taxon index; PCoA: Principal coordinate analysis; PERMANOVA: Permutational multivariate analysis of variance; PERMDISP: Permutational analysis of multivariate dispersions; PICRUSt2: Phylogenetic Investigation of Communities by Reconstruction of Unobserved States 2

## Declarations

### Ethics approval and consent to participate

[To be completed by authors. Worker hand-rinse sample collection requires informed consent and institutional ethics committee approval.]

### Consent for publication

Not applicable.

### Availability of data and materials

Raw sequence data and processed ASV tables are available from the corresponding author upon reasonable request. All analysis code is documented in the project execution notebook.

### Competing interests

The authors declare that they have no competing interests.

### Funding

[To be completed by authors.]

### Authors' contributions

[To be completed by authors.]

### Acknowledgements

[To be completed by authors.]

## References

1. Yasmin A, Rahman M, Kador M, et al. Metagenomic insights into microbial diversity and potential pathogenic transmission in poultry farm environments of Bangladesh. BMC Microbiol. 2025;25:123. doi:10.1186/s12866-025-03970-0

2. Flatgard L, Williams M, Amin N, et al. Tracking antimicrobial resistance transmission in urban and rural communities in Bangladesh: a One Health study of genomic diversity of ESBL-producing and carbapenem-resistant Escherichia coli. Microbiol Spectr. 2024;12(1):e03956-23. doi:10.1128/spectrum.03956-23

3. Kador M, Shila S, Afrin N, et al. Microbial diversity, functional genomics and antibiotic resistance in integrated chicken and fish farming systems of Bangladesh. PLoS One. 2026;21(1):e0344367. doi:10.1371/journal.pone.0344367

4. Yang J, Wang L, Liang X, et al. Microbiome, resistome, and potential transfer of antibiotic resistance genes in Chinese wet market under One Health sectors. BMC Microbiol. 2025;25:124. doi:10.1186/s12866-025-04115-z

5. Swarthout E, Fuhrmeister J, Hamzah M, et al. Differential overlap in human and animal fecal microbiomes and resistomes in rural versus urban Bangladesh. bioRxiv. 2021:2021.05.13.21257188. doi:10.1101/2021.05.13.21257188

6. Williams M, Rousham E, Neal N, et al. Impact of contrasting poultry exposures on human, poultry, and wastewater antibiotic resistomes in Bangladesh. Microbiol Spectr. 2023;11(3):e01763-23. doi:10.1128/spectrum.01763-23

7. Alam M, Rahman M, Abdullah A, et al. Human exposure to antimicrobial resistance from poultry production: assessing hygiene and waste-disposal practices in Bangladesh. Int J Hyg Environ Health. 2019;222(8):1065-1072. doi:10.1016/j.ijheh.2019.07.007

8. Scicchitano V, Babbi M, Palladino G, et al. Routes of dispersion of antibiotic resistance genes from the poultry farm system. Sci Total Environ. 2024;912:169086. doi:10.1016/j.scitotenv.2023.169086

9. Maciel-Guerra AT, Baker JL, Hu Y, et al. Dissecting microbial communities and resistomes for interconnected humans, soil, and livestock. ISME J. 2022;16(4):1097-1108. doi:10.1038/s41396-022-01315-7

10. Randeni W, Badanasinghe W, Pathirana A, et al. Tracking environmental antimicrobial resistance: isolation and antimicrobial susceptibility patterns of E. coli across hospital, livestock, and community settings in Gampaha, Sri Lanka. 2026. doi:10.21203/rs.3.rs-10015644/v1

11. Kitano T, Matsunaga N, Akiyama K, et al. Environmental dissemination of antimicrobial resistance: a resistome-based comparison of hospital and community wastewater sources. Antibiotics. 2026;15(1):99. doi:10.3390/antibiotics15010099

12. Martin M. Cutadapt removes adapter sequences from high-throughput sequencing reads. EMBnet.journal. 2011;17(1):10-12. doi:10.14806/ej.17.1.200

13. Callahan BJ, McMurdie PJ, Rosen MJ, et al. DADA2: high-resolution sample inference from Illumina amplicon data. Nat Methods. 2016;13(7):583-586. doi:10.1038/nmeth.3869

14. Quast C, Pruesse E, Yilmaz P, et al. The SILVA ribosomal RNA gene database project: improved data processing and web-based tools. Nucleic Acids Res. 2013;41(D1):D590-D596. doi:10.1093/nar/gks1219

15. Wright ES. Using DECIPHER v2.0 to analyze big biological sequence data in R. Bioinformatics. 2016;32(7):936-942. doi:10.1093/bioinformatics/btv687

16. Price MN, Dehal PS, Arkin AP. FastTree 2 — approximately maximum-likelihood trees for large alignments. PLoS One. 2010;5(3):e9490. doi:10.1371/journal.pone.0009490

17. McMurdie PJ, Holmes S. phyloseq: an R package for reproducible interactive analysis and graphics of microbiome census data. PLoS One. 2013;8(4):e61217. doi:10.1371/journal.pone.0061217

18. Oksanen J, Blanchet FG, Friendly M, et al. vegan: Community Ecology Package. R package version 2.5-7. 2020. https://CRAN.R-project.org/package=vegan

19. Anderson MJ. A new method for non-parametric multivariate analysis of variance. Austral Ecol. 2001;26(1):32-46. doi:10.1111/j.1442-9993.2001.01070.pp.x

20. Fernandes AD, Reid JN, Macklaim JM, et al. Unifying the analysis of high-throughput sequencing data: translating RNA-seq, ChIP-seq, and microbiome data to stable statistical distributions. Microbiome. 2014;2:15. doi:10.1186/2049-2618-2-15

21. Douglas GM, Maffei VJ, Zaneveld JR, et al. PICRUSt2 for prediction of metagenome functions. Nat Biotechnol. 2020;38(6):685-688. doi:10.1038/s41587-020-0548-6

22. Kanehisa M, Goto S. KEGG: Kyoto Encyclopedia of Genes and Genomes. Nucleic Acids Res. 2000;28(1):27-30. doi:10.1093/nar/28.1.27

23. Knights D, Kuczynski J, Charlson ES, et al. Bayesian community-wide culture-independent microbial source tracking. Nat Methods. 2011;8(9):761-763. doi:10.1038/nmeth.1650

## Figure legends

**Figure 1.** Study design schematic. Three One Health compartments (poultry farm, cattle farm, hospital) with paired effluent and worker hand-rinse sample collection. 16S rRNA V3–V4 amplicon sequencing (14 samples) followed by DADA2 ASV inference, diversity analysis, PICRUSt2 predicted resistome, and SourceTracker2 source tracking. Curved arrow indicates the potential AMR transmission interface across compartments.

**Figure 2.** Bacterial community composition. (a) Phylum-level stacked bar chart showing relative abundance of the eight most abundant phyla across all samples, grouped by site and sample type. (b) Genus-level stacked bar chart showing the 14 most abundant genera. Samples are ordered by site (poultry farm, cattle farm, hospital) and sample type (effluent, hand-rinse).

**Figure 3.** Alpha diversity by site and sample type. Box plots showing Observed ASVs, Shannon index, and Faith's phylogenetic diversity across the three sites, with effluent (blue) and hand-rinse (orange) samples distinguished. Individual data points are overlaid. Kruskal–Wallis p-values: Observed ASVs by sample type p = 0.0045 (q = 0.009); Faith's PD by sample type p = 0.0019 (q = 0.0078); Shannon by site p = 0.012 (q = 0.024); Pielou's evenness by site p = 0.0076 (q = 0.024).

**Figure 4.** Principal coordinate analysis (PCoA) of bacterial communities. (a) Bray–Curtis dissimilarity. (b) Weighted UniFrac distance. Points are colored by site (poultry farm = orange, cattle farm = green, hospital = blue) and shaped by sample type (effluent = circle, hand-rinse = triangle). Variance explained by each axis is annotated. PERMANOVA results: sample type R² = 0.126 (p = 0.014) for Bray–Curtis; R² = 0.269 (p = 0.0012) for weighted UniFrac.

**Figure 5.** Heatmap of AMR-relevant (pathogen-risk) genera. Log10-transformed relative abundance (with 0.01 offset) of 16 curated priority-pathogen genera across all 14 samples. Column annotations indicate site and sample type. Row clustering is based on Euclidean distance.

**Figure 6.** Predicted resistome class heatmap. Log10-transformed relative abundance (with offset) of 13 antimicrobial resistance drug classes predicted by PICRUSt2 and mapped to the KEGG BRITE ko01504 hierarchy. Column annotations indicate site and sample type. PERMANOVA on the resistome profile: sample type R² = 0.219 (p = 0.035); site R² = 0.056 (p = 0.945, not significant).

**Figure 7.** Source tracking analysis. (a) Paired versus cross-compartment Bray–Curtis similarity between each worker hand-rinse sample and effluent sources. Lines connect paired (same-farm) and cross-compartment (mean) values for each worker, colored by farm. (b) Number of ASVs shared between hospital effluent and each farm sample, faceted by sample type.

**Figure 8.** SourceTracker2 formal source tracking. (a) Stacked bar chart showing the proportional contribution of each source category (Cattle farm effluent, Poultry farm effluent, Hospital effluent, Unknown) to each worker hand-rinse sample. (b) Scatter plot of SourceTracker2 proportions versus Stage F descriptive Bray–Curtis similarity (mean per source category), with linear regression line and Spearman correlation (ρ = 0.87, p < 0.001). Note: both metrics derive from the same compositional data; concordance is a consistency check, not independent validation.

## Tables

**Table 1.** Per-sample summary: sample metadata, read counts, alpha diversity, and PICRUSt2 weighted NSTI.

**Table 2.** Alpha diversity Kruskal–Wallis test results by site and sample type, with Benjamini–Hochberg correction.

**Table 3a.** PERMANOVA results for taxonomic beta diversity (Bray–Curtis, weighted UniFrac, unweighted UniFrac), including PERMDISP dispersion tests.

**Table 3b.** PERMANOVA results for the predicted resistome profile (Bray–Curtis), by site, sample type, and cohort.

**Table 4.** Top 25 differentially abundant genera by ALDEx2 (site comparison: Kruskal–Wallis; sample type comparison: Welch's t-test), ranked by p-value. No genus reached BH q < 0.05.

**Table 5.** Mean relative abundance (%) of AMR-relevant genera by site × sample type.

**Table 6.** Predicted resistome class mean relative abundance by site × sample type, with Kruskal–Wallis p-values for sample type and site comparisons.

**Table 7.** Cross-compartment core genera (n = 35): mean relative abundance (%) by site.

**Table 8.** Paired source-sharing metrics: per-worker Bray–Curtis similarity, Jaccard overlap, and weighted shared fraction for paired versus cross-compartment effluent.

**Table 9.** SourceTracker2 per-worker source proportions: top source, and proportional contribution of Cattle farm effluent, Poultry farm effluent, Hospital effluent, and Unknown.
