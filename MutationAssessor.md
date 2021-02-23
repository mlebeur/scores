# Name

MutationAssessor

# Version

release 3

# Usefull for

# Short description

MutationAssessor predicts the functional impact of amino-acid substitutions in proteins using the evolutionary conservation of the affected amino acid in protein homologs.

# Orientation and range

We display the prediction, which is one of 'neutral', 'low', 'medium' and 'high', and the rank score, which is between 0 and 1 where variants with higher scores are more likely to be deleterious. 

The MAori score ranges from -5.135 to 6.49.

| Range | functional impact of a variant |
| 3.5 to 6.49 | High (H) |
| 1.935 to 3.5 | Medium (M) |
| 0.8 yo 1.935 | Low (L) |
| -5.135 yo 0.8 | neutral (N) |

The rankscoreranges from 0 to 1.

| Range | functional impact of a variant |
| 0.92922 to 1 | High (H) |
| 0.51944 to 0.92922 | Medium (M) |
| 0.19719 to 0.51944 | Low (L) |
| 0 to 0.19719 | neutral (N) |

The prediction.

| Predicted | functional impact of a variant |
| functional | high ("H") or medium ("M") |
| non-functional | low ("L") or neutral ("N") | 

# Methodology

In our approach, called combinatorial entropy optimization (CEO), we optimize a conservation contrast function over different assignments (clusterings) of proteins to subfamilies. Hierarchical clustering [19] is used to explore the space of alternative clusterings over a diverse set of clustering trajectories to reach an optimum. Given an optimal clustering, individual residue positions (columns) vary considerably in the value of the combinatorial entropy. The distribution of column entropy values is a z-shaped curve and, reassuringly, is drastically different from the corresponding distribution for randomized alignments. Different entropy values are interpreted to reflect different residue-specific functional constraints, and residues with lowest entropy values are predicted to be functional.

# VCF description (VEP)

`##MutationAssessor_UniprotID=(from dbNSFP) Uniprot ID number provided by MutationAssessor.`

`##MutationAssessor_pred=(from dbNSFP) MutationAssessor's functional impact of a variant : predicted functional, i.e. high ("H") or medium ("M"), or predicted non-functional, i.e. low ("L") or neutral ("N"). The MAori score cutoffs between "H" and "M", "M" and "L", and "L" and "N", are 3.5, 1.935 and 0.8, respectively. The rankscore cutoffs between "H" and "M", "M" and "L", and "L" and "N", are 0.92922, 0.51944 and 0.19719, respectively.`

`##MutationAssessor_score=(from dbNSFP) MutationAssessor functional impact combined score (MAori). The score ranges from -5.135 to 6.49 in dbNSFP.`

`##MutationAssessor_score_rankscore=MutationAssessor_score_rankscore from dbNSFP file`

`##MutationAssessor_variant=(from dbNSFP) AA variant as to MutationAssessor_UniprotID.`

# Long Description

# Exemple

# Source

[dbNSFP](https://sites.google.com/site/jpopgen/dbNSFP)

[Publication](https://academic.oup.com/nar/article/39/17/e118/2411278)

[Site](http://mutationassessor.org/r3/)
