# Name

SIFT (Sorting Intolerant From Tolerant)

# Version

version 5.2.2

# Usefull for

# Short description

SIFT predicts whether an amino acid substitution is likely to affect protein function based on sequence homology and the physico-chemical similarity between the alternate amino acids. The data provide for each amino acid substitution is a score and a qualitative prediction (either 'tolerated' or 'deleterious').

# Orientation and range

The score is the normalized probability that the amino acid change is tolerated so scores nearer zero are more likely to be deleterious.

VEP configuration

| SIFT value | Qualitative prediction |
| Less than 0.05 | "Deleterious" |
| Greater than or equal to 0.05 | "Tolerated" | 

Ion torrent configuration

| SIFT value | Qualitative prediction |
| Less than 0.05 | "Deleterious" | 
| Greater than or equal to 0.05 | "Tolerated" |

# Methodology

SIFT takes a query sequence and uses multiple alignment information to predict tolerated and deleterious substitutions for every position of the query sequence. SIFT is a multistep procedure that, given a protein sequence, (1) searches for similar sequences, (2) chooses closely related sequences that may share similar function, (3) obtains the multiple alignment of these chosen sequences, and (4) calculates normalized probabilities for all possible substitutions at each position from the alignment. Substitutions at each position with normalized probabilities less than a chosen cutoff are predicted to be deleterious; those greater than or equal to the cutoff are predicted to be tolerated.

# VCF description (VEP)

`##SIFT_converted_rankscore=(from dbNSFP) SIFTori scores were first converted to SIFTnew=1-SIFTori, then ranked among all SIFTnew scores in dbNSFP. The rankscore is the ratio of the rank the SIFTnew score over the total number of SIFTnew scores in dbNSFP. If there are multiple scores, only the most damaging (largest) rankscore is presented. The rankscores range from 0.00963 to 0.91219.`

`##SIFT_pred=(from dbNSFP) If SIFTori is smaller than 0.05 (rankscore>0.395) the corresponding nsSNV is predicted as "D(amaging)"; otherwise it is predicted as "T(olerated)". Multiple predictions separated by ";"`

`##SIFT_score=(from dbNSFP) SIFT score (SIFTori). Scores range from 0 to 1. The smaller the score the more likely the SNP has damaging effect. Multiple scores separated by ";", corresponding to Ensembl_proteinid.`

# Long Description

See Methods in the [Publication](https://pubmed.ncbi.nlm.nih.gov/12824425/)

# Schema

# Exemple

# Source

[dbNSFP](https://sites.google.com/site/jpopgen/dbNSFP)

[Publication](https://pubmed.ncbi.nlm.nih.gov/12824425/)

[Site](https://sift.bii.a-star.edu.sg/)

