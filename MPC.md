# Name

MPC (Missense badness, PolyPhen-2, and Constraint)

# Version

v1

# Usefull for

Functionnal effect

# Short description

MPC_score is a deleteriousness prediction score for missense variants based on regional missense constraint.

# Orientation and range

MPC_score ranges from 0 to 5.

The larger the score, the more likely the variant is pathogenic.

The advise threshold is MPC >= 2.

MPC_rankscore ranges from 0 to 1.

# Methodology

Use logistic regression on missense badness, PolyPhen-219, BLOSUM24, and Grantham scores to predict deleteriousness.


# VCF description (VEP)

`## MPC_score: A deleteriousness prediction score for missense variants based on regional missense constraint. The range of MPC score is 0 to 5. The larger the score, the more likely the variant is pathogenic. Details see doi: http://dx.doi.org/10.1101/148353. Multiple entries are separated by ";", corresponding to Ensembl_transcriptid.`

`## MPC_rankscore: MPC scores were ranked among all MPC scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of MPC scores in dbNSFP.`



# Long Description


# Training dataset

ExAC data on protein coding genes


# Testing dataset 


# Exemple


# Schema

# Source


[Publication](https://www.biorxiv.org/content/10.1101/148353v1.full.pdf)


