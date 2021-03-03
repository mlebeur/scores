# Name

SiPhy

# Version

1

#Usefull for

Pahtogenicity

# Short description:

SiPhy is a conservation score based on 29 mammals genomes multialinments that takes the type of mutation into account.

# Orientation and range:

Higher scores indicate higher conservation.

SiPhy_29way_logOdds ranges from 0 to 37.9718.

The advise threshold is 12.

SiPhy_29way_logOdds_rankscore ranges from 0 to 1.

# Methodology

From a multiple alignment file and neutral "average" evolutionary model file (PHAST / PALM).

Siphy estimate the local rate of variation (ω) by sliding a fixed-size window or by providing a set of annotations.

SiPhy estimates substitution patterns [π in Equation (10) of Garber, et al.] per column, essentially using a fixed-size window of length 1. SiPhy then sums the resulting scores to estimate substitution patterns across larger fixed-size windows. 

So the ouput contains Log-odds ratio of the fitted vs the neutral likelihodds (SiPhy writes negative likelihodds for ω greater than 1 to distinguish rapid vs slow evolving sequence).

# Training dataset

[ENCODE regions (Birney et al., 2007)](https://pubmed.ncbi.nlm.nih.gov/17571346/)

# VCF description (VEP)

`##SiPhy_29way_logOdds=(from dbNSFP) SiPhy score based on 29 mammals genomes. The larger the score, the more conserved the site. Scores range from 0 to 37.9718 in dbNSFP.`

`##SiPhy_29way_logOdds_rankscore=(from dbNSFP) SiPhy_29way_logOdds scores were ranked among all SiPhy_29way_logOdds scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of SiPhy_29way_logOdds scores in dbNSFP.`

`##SiPhy_29way_pi=(from dbNSFP) The estimated stationary distribution of A, C, G and T at the site, using SiPhy algorithm based on 29 mammals genomes.`

# Long Description

Statistical method for modeling the evolution of sequence under selective constraint. The method works by examining the pattern of base substitutions at each site, rather than the rate of substitutions as all previous methods do.

# Schema

[Figure 4](https://academic.oup.com/bioinformatics/article/25/12/i54/187307)

# Exemple

# Source

[Site](http://portals.broadinstitute.org/genome_bio/siphy/index.html)

[Publication](https://academic.oup.com/bioinformatics/article/25/12/i54/187307)

