# Name

MVP (Missense Variant Pathogenicity prediction)

# Version

v1.0

# Usefull for

Functionnal effect

# Short description

MVP is a pathogenicity prediction score for missense variants using deep learning approach.

# Orientation and range

MVP_score ranges from 0 to 1.

The larger the score, the more likely the variant is pathogenic.

| Thresholds | ExAC pLI | Flag | 
| - | - | - |
| > 0.7 | >= 0.5 | D(amaging) |
| < 0.7 | >= 0.5 | T(olerant) |
| > 0.75 | < 0.5 | D(amaging) |
| < 0.75 | < 0.5 | T(olerant) |

# Methodology

# VCF description (VEP)

`##MVP_score: A pathogenicity prediction score for missense variants using deep learning approach. The range of MVP score is from 0 to 1. The larger the score, the more likely the variant is pathogenic. The authors suggest thresholds of 0.7 and 0.75 for separating damaging vs tolerant variants in constrained genes (ExAC pLI >=0.5) and non-constrained genes (ExAC pLI<0.5), respectively. Details see doi: http://dx.doi.org/10.1101/259390 Multiple entries are separated by ";", corresponding to Ensembl_transcriptid.`

`##MVP_rankscore: MVP scores were ranked among all MVP scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of MVP scores in dbNSFP.`

# Long Description

## Features used in the MVP model

### local context:

GC content within 10 flanking bases on the reference genome.

### amino acid constraint

Blosum62 and pam250.

### conservation scores

PhyloP 20way mammalian and 100way vertebrate, GERP++, SiPhy 29way, and phastCons 20way mammalian and 100way vertebrate

### Protein structure, interaction, and modifications

Predicted secondary structures, number of protein interactions from the BioPlex 2.0 Network, whether the protein is involved in complexes formation from CORUM database, number of high-confidence interacting proteins by PrePPI, probability of a residue being located the interaction interface by PrePPI (based on PPISP, PINUP, PredU), predicted accessible surface areas were obtained from dbPTM, SUMO scores in 7-amino acids neighborhood by GPS-SUMO, phosphorylation sites predictions within 7 amino acids neighborhood by GPS3.0, and ubiquitination scores within 14-amino acids neighborhood by UbiProber.

### Gene mutation intolerance

ExAC metrics (pLI, pRec, lof_z) designed to measure gene dosage sensitivity or haploinsufficiency, RVIS, probability of causing diseases under a dominant model “domino”, average selection coefficient of loss of function variants in a gene “s_het”, and sub-genic regional depletion of missense variants.

### Selected deleterious or pathogenicity scores by previous published methods obtained through dbNSFPv3.3a

Eigen, VEST, MutationTaster, PolyPhen2, SIFT, PROVEAN, fathmm-MKL, FATHMM, MutationAssessor, and LRT.

## Deep learning model

MVP is based on a deep residual neural network model (ResNet)22 for predicting pathogenicity using the predictors described above. To preserve the structured features in training data, we ordered the features according to their correlations (Supplementary Fig. 3). The model (Supplementary Fig. 2) takes a vector of the ordered features as input, followed by a convolutional layer of 32 kernels with size 3x1 and stride of 1, then followed by 2 computational residual units, each consisting of 2 convolutional layers of 32 kernels with size 3x1 and stride of 1 and a ReLU activation layer in between. The output layer and input layer of the residual unit is summed and passed on to a ReLU activation layer. After the two convolutional layers with residual connections, 2 fully connected layers of 320x512 and 512x1 are used followed by a sigmoid function to generate the final output.

# Training dataset

22,390 missense mutations from Human Gene Mutation Database Pro version 2013 (HGMD) database under the disease mutation (DM) category, 12,875 deleterious variants from UniProt, and 4424 pathogenic variants from ClinVar database as true positive (TP). In total, there are 32,074 unique positive training variants. The negative training sets include 5190 neutral variants from Uniprot, randomly selected 42,415 rare variants from DiscovEHR database, and 39,593 observed human-derived variants. In total, there are 86,620 unique negative training variants.

# Testing dataset 

The three categories are: (a) Benchmark data sets from VariBench as positives and randomly selected rare variants from DiscovEHR database as negatives; (b) cancer somatic missense mutations located in hotspots from recent study as positives and randomly selected rare variants from DiscovEHR database as negatives; (c) and de novo missense mutation data sets from recent published exome-sequencing studies. All variants in (a) and (b) that overlap with training data sets were excluded from testing.

# Exemple


# Schema


# Source

[Publication](http://dx.doi.org/10.1101/259390)

