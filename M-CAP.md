# Name

M-CAP (The Mendelian Clinically Applicable Pathogenicity)

# Version

v1.3

# Usefull for

Pahogenicity

# Short description

M-CAP is a pathogenicity classifier for rare missense variants in the human genome y combining previous pathogenicity scores (including SIFT, Polyphen-2 and CADD) with novel features and a powerful model, we attain the best classifier at all thresholds, reducing a typical exome/genome rare (<1%) missense variant (VUS) list from 300 to 120, while never mistaking 95% of known pathogenic variants as benign.

# Orientation and range

M-CAP_score ranges from 0 to 1.

The larger the score the more likely the SNP has damaging effect.

| M-CAP_score | M-CAP_pred |
| - | - |
| < 0.025 | T(olerated) |
| > 0.025 | D(amaging) |

# Methodology

## Extract features for kearning algorithm

M-CAP uses both preexisting and new features for each missense variant. It uses nine established pathogenicity likelihood scores: SIFT, PolyPhen-2, CADD, MutationTaster, MutationAssessor, FATHMM, LRT, MetaLR, and MetaSVM. It also incorporates seven established measures of base-pair, amino acid, genomic region, and gene conservation: RVIS24, PhyloP25, PhastCons26, PAM250, BLOSUM62, SIPHY28, and GERP29. In addition, M-CAP introduces 298 new features derived from multiple-sequence alignment of 99 primate, mammalian, and vertebrate genomes to the human genome. Three vectors of 99 binary features indicate whether each species has the human reference amino acid, the alternative amino acid, or no amino acid aligning. One integer feature counts the number of different amino acids observed at the codon across the 100 species.

## Training the data

See Training set section.

## M-CAP learning

M-CAP uses a gradient boosting tree classifier17, which learns a function of the input features as a linear combination of decision trees, each derived iteratively to correct previously misclassified elements. The model hyperparameters were optimized with a systematic grid search.

# VCF description (VEP)

`##M-CAP_pred=(from dbNSFP) Prediction of M-CAP score based on the authors' recommendation, "T(olerated)" or "D(amaging)". The score cutoff between "D" and "T" is 0.025.`

`##M-CAP_rankscore=(from dbNSFP) M-CAP scores were ranked among all M-CAP scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of M-CAP scores in dbNSFP.`

`##M-CAP_score=(from dbNSFP) M-CAP score (details in DOI: 10.1038/ng.3703). Scores range from 0 to 1. The larger the score the more likely the SNP has damaging effect.`


# Long Description

The Mendelian Clinically Applicable Pathogenicity (M-CAP) score is a pathogenicity likelihood score that aims to misclassify no more than 5% of pathogenic variants while aggressively reducing the list of variants of uncertain significance. Much like allele frequency, M-CAP is readily interpreted; if it classifies a variant as benign, then that variant can be trusted to be benign with high confidence. M-CAP uses gradient boosting trees, a supervised learning classifier that excels at analyzing nonlinear interactions between features, and has state-of-the-art performance in a variety of classification tasks. The features M-CAP uses for classification are based on both existing pathogenicity likelihood scores and direct measures of evolutionary conservation, the cross-species analog to frequency within the human population. We provide both a novel method that combines amino acid conservation features with gradient boosting trees that can be applied to any variant training set and computed scores trained on mutations linked to Mendelian diseases that can be directly used by clinicians to interpret variants of uncertain consequences.

# Training set

Rare SNVs from HGMD Pro version 2015.2, 1000G, patient exomes and Mendelian mutations associated with BRCA1, BRCA2, CFTR, MLL2.

| | HGMD Pro 2015.2 (pathogenic) | ExAC v3 (benign) | Patient exomes (median) |
| - | - | - | - | 
| Single-nucleotide variants | 104,282 | 9,291,050 | 165,934 |
| Missense variants | 70,192 | 3,428,124 | 9,724 |
| Rare (≤1%) missense variants (training data) | 63,418 | 3,287,432 | 305 |
| Variants after removal of overlap with HGMD | N/R | 3,268,665 | N/R | 
| Variants after exclusion of those used for training  | 12,418 | 3,137,919  |  259 | 

# Exemple

# Schema

# Source

[Site](http://bejerano.stanford.edu/MCAP/)

[Publication](https://www.nature.com/articles/ng.3703.epdf?author_access_token=QpYcDWHWC2sC08xquy51RtRgN0jAjWel9jnR3ZoTv0NW_LUqRr20bAF4DHicakv7aAze4axhulp3iw7_FiWtLJK80EJeraUYDseDG607CfszMjiK1pq2G7wodelPyGeQ)

