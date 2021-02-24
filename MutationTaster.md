MutationTaster

# Version

1

# Usefull for

Pathogenicity

# Short description

MutationTaster evaluates disease-causing potential of sequence alterations using evolutionary conservation, splice-site changes, loss of protein features and changes that might affect the amount of mRNA.

# Orientation and range

MutationTaster score ranges from 0 to 1.

| MutationTaster prediction | score |
| - | - |
| "A" ("disease_causing_automatic") | > 0.5 | 
| "D" ("disease_causing") | > 0.5 |
| "N" ("polymorphism") | < 0.5 |
| "P" ("polymorphism_automatic") | < 0.5 |

MutationTaster converted rankscore range from 0.08979 to 0.81033.

| MutationTaster converted rankscore | score |
| - | - |
| "A" ("disease_causing_automatic") | > 0.31713 | 
| "D" ("disease_causing") | > 0.31713 |
| "N" ("polymorphism") | < 0.31713 |
| "P" ("polymorphism_automatic") | < 0.31713 |

# Methodology

# VCF description (VEP)

`##MutationTaster_AAE=(from dbNSFP) MutationTaster predicted amino acid change.`

`##MutationTaster_converted_rankscore=(from dbNSFP) The MTori scores were first converted: if the prediction is "A" or "D" MTnew=MTori; if the prediction is "N" or "P", MTnew=1-MTori. Then MTnew scores were ranked among all MTnew scores in dbNSFP. If there are multiple scores of a SNV, only the largest MTnew was used in ranking. The rankscore is the ratio of the rank of the score over the total number of MTnew scores in dbNSFP. The scores range from 0.08979 to 0.81033.`

`##MutationTaster_model=(from dbNSFP) MutationTaster prediction models.`

`##MutationTaster_pred=(from dbNSFP) MutationTaster prediction, "A" ("disease_causing_automatic"), "D" ("disease_causing"), "N" ("polymorphism") or "P" ("polymorphism_automatic"). The score cutoff between "D" and "N" is 0.5 for MTnew and 0.31713 for the rankscore.`

`##MutationTaster_score=(from dbNSFP) MutationTaster p-value (MTori), ranges from 0 to 1. Multiple scores are separated by ";". Information on corresponding transcript(s) can be found by querying http://www.mutationtaster.org/ChrPos.html`

# Long Description

MutationTaster integrates information from different biomedical databases and uses established analysis tools (Supplementary Methods). Analyses comprise evolutionary conservation, splice-site changes, loss of protein features and changes that might affect the amount of mRNA. Test results are then evaluated by a naive Bayes classifier2, which predicts the disease potential. A typical query is completed in less than 0.3 seconds.

Depending on the nature of the alteration, MutationTaster chooses between three different prediction models, which are either aimed at 'silent' synonymous or intronic alterations (without_aae), at alterations affecting a single amino acid (simple_aae) or at alterations causing complex changes in the amino acid sequence (complex_aae).

To train the classifier, we generated a dataset with all available and suitable common polymorphisms and known disease-causing mutations extracted from common databases and the literature.

# Exemple

[Tutorial](http://www.mutationtaster.org/examples/tutorial.html)

# Warnings

Present limitations of the software comprise its inability to analyze insertion-deletions greater than 12 base pairs and alterations spanning an intron-exon border. 

Also, analysis of non-exonic alterations is restricted to Kozak consensus sequence, splice sites and poly(A) signal.

# Source

[Site](http://www.mutationtaster.org/)

[Publication](https://www.nature.com/articles/nmeth0810-575)
