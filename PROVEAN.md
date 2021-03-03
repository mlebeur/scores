# Name

PROVEAN

# Version

1.1 ensembl 66

# Usefull for

Pahogenicity

# Short description

PROVEAN (Protein Variation Effect Analyzer) is a software tool which predicts whether an amino acid substitution or indel has an impact on the biological function of a protein

# Orientation and range

PROVEAN_score ranges from -14 to 14.

The smaller the score the more likely the SNP has damaging effect.

PROVEAN_converted_rankscore ranges from 0 to 1. It has been calculated as  PROVEANnew=1-(PROVEANori+14)/28 before to be ranked on dbNSFP.

| PROVEAN_score | PROVEAN_converted_rankscore | PROVEAN_pred |
| - | - | - |
| <= -2.5 | >=0.543 | D(amaging) |
| > -2.5 | <0.543 | N(eutral) |

# Methodology

## Homology and clustering

In the first step, PROVEAN collects a set of homologous and distantly related sequences from the NCBI NR protein database (released August 2011) using BLASTP (ver.2.2.25) with an E-value threshold of 0.1

The sequences are clustered based on a sequence identity of 80% to remove redundancy using the CD-HIT program (ver.4.5.5).

Starting from the sequence cluster most similar to the query sequence, the clusters are added to the supporting sequence set one by one until there is a sufficient number of clusters in the supporting set.

## Scoring and predicting

In the second step, for each sequence in the supporting sequence set, a delta score is computed using the BLOSUM62 substitution matrix and gap penalties of 10 for opening and 1 for extension. 

Within each cluster, an average delta score is computed.

The averaged delta scores are again averaged among all clusters so that each cluster is weighted equally.

This unbiased averaged delta score is the final PROVEAN score

# VCF description (VEP)

`##PROVEAN_converted_rankscore=(from dbNSFP) PROVEANori were first converted to PROVEANnew=1-(PROVEANori+14)/28, then ranked among all PROVEANnew scores in dbNSFP. The rankscore is the ratio of the rank the PROVEANnew score over the total number of PROVEANnew scores in dbNSFP. If there are multiple scores, only the most damaging (largest) rankscore is presented. The scores range from 0 to 1.`

`##PROVEAN_pred=(from dbNSFP) If PROVEANori <= -2.5 (rankscore>=0.543) the corresponding nsSNV is predicted as "D(amaging)"; otherwise it is predicted as "N(eutral)". Multiple predictions separated by ";", corresponding to Ensembl_proteinid.`

`##PROVEAN_score=(from dbNSFP) PROVEAN score (PROVEANori). Scores range from -14 to 14. The smaller the score the more likely the SNP has damaging effect. Multiple scores separated by ";", corresponding to Ensembl_proteinid.`

# Long Description

PROVEAN is an alignment-based score computed a metric to predict the damaging effects of variations not limited to single amino acid substitutions but also in-frame insertions, deletions, and multiple amino acid substitutions. This alignment-based score measures the change in sequence similarity of a query sequence to a protein sequence homolog before and after the introduction of an amino acid variation to the query sequence.

# Training data

SNVs from UniProt (Release 2011_09) and experimental datasets from mutagenesis experiments, previously carried out for the E.coli LacI protein (Markiewicz et al. 1994) and the human, tumor suppressor TP53 protein

# Schema

[Figure 2](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0046688)

# Exemple

# Source

[Publication](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0046688)

[Site](http://provean.jcvi.org/index.php)
