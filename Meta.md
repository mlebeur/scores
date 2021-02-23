# Name

Meta (MetaLR or MetaSVM)

# Version

1

# Usefull for



# Short description

MetaLR uses logistic regression or support vector machine to integrate nine independent variant deleteriousness scores and allele frequency information to predict the deleteriousness of missense variants. 

# Orientation and range

Variants are classified as 'tolerated' or 'damaging'.

MetaLR uses logistic regression to integrate nine independent variant deleteriousness scores and allele frequency information to predict the deleteriousness of missense variants. Variants are classified as 'tolerated' or 'damaging'; a score between 0 and 1 is also provided and variants with higher scores are more likely to be deleterious. 

# Methodology 

To construct our own ensemble scores, we used these nine scores (SIFT, PolyPhen-2, GERP++, MutationTaster, Mutation Assessor, FATHMM, LRT, SiPhy and PhyloP) for all potential human nsSNVs collected in the dbNSFP database, along with the MMAF observed in diverse populations of the 1000 Genomes project (32), as our component scores. After imputing missing values for observations in training dataset, we employed SVM and LR algorithms for computing these two ensemble scores and evaluated three kernel functions (linear, radial and polynomial kernel) for the SVM approach, all based on default parameters 

# VCF description (VEP)

`##MetaLR_pred=(from dbNSFP) Prediction of our MetaLR based ensemble prediction score,"T(olerated)" or "D(amaging)". The score cutoff between "D" and "T" is 0.5. The rankscore cutoff between "D" and "T" is 0.81113.`

`##MetaLR_rankscore=(from dbNSFP) MetaLR scores were ranked among all MetaLR scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of MetaLR scores in dbNSFP. The scores range from 0 to 1.`

`##MetaLR_score=(from dbNSFP) Our logistic regression (LR) based ensemble prediction score, which incorporated 10 scores (SIFT, PolyPhen-2 HDIV, PolyPhen-2 HVAR, GERP++, MutationTaster, Mutation Assessor, FATHMM, LRT, SiPhy, PhyloP) and the maximum frequency observed in the 1000 genomes populations. Larger value means the SNV is more likely to be damaging. Scores range from 0 to 1.`

# Long Description

MetaSVM and MetaLR are based on 10 component scores (SIFT, PolyPhen-2 HDIV, PolyPhen-2 HVAR, GERP++, MutationTaster, Mutation Assessor, FATHMM, LRT, SiPhy, PhyloP) and the maximum frequency observed in the 1000 genomes populations.

Training dataset is composed of 14 191 deleterious mutations as true positive (TP) observations and 22 001 neutral mutations as true negative (TN) observations, all based on the Uniprot database.

Note that the TN observations contain both common [maximum minor allele frequency (MMAF) >1% in diverse populations of the 1000 Genomes project] and rare (MMAF ≤1%) variants to ensure the generalizability of our model.

# Exemple

# Source

[dbNSFP](https://sites.google.com/site/jpopgen/dbNSFP)

[publication](https://academic.oup.com/hmg/article/24/8/2125/651446)

