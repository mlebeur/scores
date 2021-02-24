# Name

VEST (Variant Effect Scoring Tool)

# Version

3.0

# Usefull for

# Short description

Variant Effect Scoring Tool (VEST), a supervised machine learning-based classifier, to prioritize rare missense variants with likely involvement in human disease.

# Orientation and range

VEST3 score and rankscore range from 0 to 1.

The larger theses scores are the more likely the mutation may cause functional change.

# Methodology

A Random Forest classifier (ntrees = 1000, mtry = 9) was trained on 47724 missense mutations directly implicated in human inherited disease from the Human Gene Mutation Database (HGMD Professional v2012.2), and 45818 likely neutral missense mutations from the Exome Sequencing Project (ESP6500 accessed 07/2012) using parf Parallel Random Forest software http://code.google.com/p/parf/. Each mutation was described by a vector of 86 quantitative features available through the SNVBox database. HGMD disease mutations were filtered so as to exclude polymorphisms, low-confidence disease mutations and common variants (AF ≥ 1%). This filtering strategy removed 3592 polymorphisms, 4739 low confidence mutations and 492 common variants. An additional 14181 variants that did not cause missense changes were also removed. Twenty-three of the remaining variants did not have a RefSeq accession associated with the variant, 321 consisted of different genomic events that resulted in the identical missense mutation and 47 could not be annotated with features from the SNVBox because the transcript identifier was not supported. ESP6500 mutations were filtered to remove rare variants (AF <1%), and any mutations occurring at the same codon as an HGMD disease mutation were dropped. Removing overlap with HGMD resulted in 689823 missense variants, only 46303 of which were present at (AF <1%) and mapped onto a RefSeq NM identifier. An additional 485 ESP6500 mutations could not be annotated with features from SNVBox because the transcript identifier was not supported.

# VCF description (VEP)

`##VEST3_rankscore=(from dbNSFP) VEST3 scores were ranked among all VEST3 scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of VEST3 scores in dbNSFP. In case there are multiple scores for the same variant, the largest score (most damaging) is presented. The scores range from 0 to 1. Please note VEST score is free for non-commercial use. For more details please refer to http://wiki.chasmsoftware.org/index.php/SoftwareLicense. Commercial users should contact the Johns Hopkins Technology Transfer office.`

`##VEST3_score=(from dbNSFP) VEST 3.0 score. Score ranges from 0 to 1. The larger the score the more likely the mutation may cause functional change. Multiple scores separated by ";", corresponding to Transcript_id_VEST3. Please note this score is free for non-commercial use. For more details please refer to http://wiki.chasmsoftware.org/index.php/SoftwareLicense. Commercial users should contact the Johns Hopkins Technology Transfer office.`

# Long Description

The Variant Effect Scoring Tool (VEST) is a new method for prioritizing missense mutations that alter protein activity. VEST uses a supervised machine learning algorithm, Random Forest, to identify likely functional missense mutations. The training set is a positive class of missense variants from the Human Gene Mutation Database and a negative class of common missense variants detected in the Exome Sequencing Project (ESP) population. An allele frequency of 1% or higher is considered common for this work. All mutations are described by a set of 86 quantitative features.

Although the VEST training set is designed to identify missense mutations that alter protein activity, its construction includes the additional context of selective difference between disease and common variants. The disease class from HGMD is enriched for variants under purifying selection, whereas the neutral class from ESP common variants includes variants under positive selection in the human population in addition to truly neutral variants. If we assume that the VEST classifier can generalize to mutations not in its training set, it should be able to take a set of variants from a sequenced exome and prioritize functional mutations which are similar to disease mutations over those which are similar to neutral mutations or to functional mutations under positive selection.

# Exemple

[Site](https://karchinlab.org/apps/vest/demo.pdf)

# Schema

# Training set

A Random Forest classifier (ntrees = 1000, mtry = 9) was trained on 47724 missense mutations directly implicated in human inherited disease from the Human Gene Mutation Database (HGMD Professional v2012.2), and 45818 likely neutral missense mutations from the Exome Sequencing Project (ESP6500 accessed 07/2012) using parf Parallel Random Forest software.

# Source

[Publication](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3665549/)

[Publication VEST-INDEL](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3665549/)
