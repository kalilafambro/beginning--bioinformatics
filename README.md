# beginning--bioinformatics
beginning bioinformatics course code 
Kalila Fambro + 1002352833 + BIOL5340-001



# Benchmarking BLAST and k-mer machine learning for Fusarium species-complex identification from EF-1α sequences

Bioinformatics final project (solo), draft stage.

## Question
Does a 6-mer logistic regression match BLAST top-hit classification of Fusarium species complexes from EF-1α (TEF1) sequences, and how does each degrade when sequences are truncated?

## Data
NCBI GenBank EF-1α records retrieved with Biopython Entrez, labelled by species complex (FSSC, FOSC, GFSC, FIESC). FDSC was excluded (5 sequences, 2 studies). See `results/curated_metadata.csv` for accessions and labels. No data are stored beyond accessions and derived tables.

## How to run
1. Open `Fusarium_EF1a_BLAST_vs_kmer.ipynb` in Google Colab.
2. In the config cell set `EMAIL` to your email and `DEMO = False` (True runs a synthetic demo).
3. Run all cells top to bottom (the GenBank download takes several minutes).
4. Outputs are written to `results/`.

## Contents
- `Fusarium_EF1a_BLAST_vs_kmer.ipynb`: full analysis
- `results/metrics.csv`: accuracy and macro-F1 with bootstrap CIs
- `results/accuracy_by_identity_bin.csv`: accuracy by BLAST % identity
- `results/curated_metadata.csv`: curated records
- `results/` figures: accuracy vs. truncation length, confusion matrices
- `ai_usage.md`: AI-use log

## Methods in brief
Study-level train/test split (231 train / 126 test sequences). BLAST database built from training sequences only; ties and no-hit count as errors. 6-mer count features, L2 normalized, class-balanced logistic regression (C tuned by study-grouped CV). Truncation to 100/75/50% of length; all truncated copies of a sequence stay together. 95% bootstrap CIs over original sequences.

## Status
Done: data curation, BLAST and k-mer models, truncation to 50%, bootstrap, figures, similarity-bin check. To do: 25% and 10% truncation, final report and presentation.

## Software versions
Python [version], Biopython [version], scikit-learn [version], BLAST+ [version].

## References
Altschul et al. (1990); Camacho et al. (2009); Cock et al. (2009); O'Donnell et al. (2010); Pedregosa et al. (2011); Sayers et al. (2024); Thomas et al. (2019). Full list in the report.
