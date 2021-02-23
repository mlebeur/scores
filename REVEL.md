
# Name

REVEL

# Version

1

#Usefull for

Pahtogenicity

# Short description:

The Rare Exome Variant Ensemble Learner REVEL is an ensemble method for predicting the pathogenicity of missense variants. It integrates scores from MutPred, FATHMM v2.3, VEST 3.0, PolyPhen-2, SIFT, PROVEAN, MutationAssessor, MutationTaster, LRT, GERP++, SiPhy, phyloP, and phastCons

# Orientation and range:

* Score range from 0 to 1 and variants with higher scores are predicted to be more likely to be pathogenic.

* REVEL does not provide a descriptive prediction but for convenience, VEP display scores above 0.5, as 'likely disease causing' and display scores below 0.5 as 'likely benign'.

* It was estimated that 75.4% of disease mutations but only 10.9% of neutral variants have a score above 0.5.

# Methodology

REVEL incorporates a total of 18 individual pathogenicity prediction scores from 13 tools as predictive features. MutPred scores were newly computed for this study with the UniProt canonical protein sequence when available and the Ensembl canonical transcript otherwise. PROVEAN scores were obtained from dbNSFP v2.9 (February 3, 2015). 16 additional scores were obtained from dbNSFP v2.7 (September 12, 2014), including eight functional prediction scores (SIFT, PolyPhen-2 HVAR and HDIV, LRT, MutationTaster, MutationAssessor, FATHMM v2.3, and VEST 3.0) and eight conservation scores (GERP++, SiPhy, three phyloP scores for primates, placental mammals, and vertebrates, and three phastCons scores for primates, placental mammals, and vertebrates). For PolyPhen-2, FATHMM, and PROVEAN, when multiple protein isoforms were associated with a given variant, we used the average score across all isoforms. Missing features were imputed with the k-nearest neighbors method implemented in the R “impute” package. 

Missing feature values for a given variant were assigned the average value of the non-missing values of that feature from its k = 40 nearest neighboring variants; when more than 50% of features were missing for a given variant, we assigned to each missing feature its overall mean across all variants.

# Training dataset

REVEL was trained with putative rare neutral and disease missense variants. Disease variants were obtained from the Human Gene Mutation Database (HGMD) version 2015.2 and were restricted to the set of missense disease mutations (DMs) added to HGMD since August 1, 2012 to minimize overlap with variants previously used to train component features in the REVEL random forest. Missense exome sequencing variants (ESVs) were obtained from the Exome Sequencing Project (ESP) European-American and African-American populations, the Atherosclerosis Risk in Communities (ARIC) study European-American and African American populations, and the 1000 Genomes Project (KGP) European, Yoruban, and Asian populations, as recorded in dbNSFP version 2.7. After excluding all disease variants in HGMD and the data sources for test sets 1 and 2 described below, the remaining missense ESVs were considered putatively neutral. For both the disease and neutral training variants, we also excluded all variants that had previously been used to train individual component features in the REVEL random forest; specifically, MutPred, PolyPhen-2, MutationTaster, FATHMM v2.3, and VEST 3.0.

Finally, when a given genetic variant corresponded to multiple amino acid substitutions (AASs) at the protein level, only one AAS was selected at random. After applying all exclusion criteria, a total of 6,182 disease variants and 281,972 putatively neutral ESVs remained. We randomly selected approximately half (n = 140,921) of the putatively neutral ESVs, of which 123,706 rare ESVs (with a maximum alternate AF between 0.1% and 1% across the seven study populations) were used for training, and 17,215 ESVs with an AF >1% were used for initial evaluation of performance across a range of AFs. The remaining half of ESVs were held out for use as independent test variants as described below. Thus, the final training set consisted of 6,182 HGMD disease variants and 123,706 rare neutral ESVs.


# VCF description (VEP)

`##REVEL_rankscore=(from dbNSFP) REVEL scores were ranked among all REVEL scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of REVEL scores in dbNSFP.`

`##REVEL_score=(from dbNSFP) REVEL is an ensemble score based on 13 individual scores for predicting the pathogenicity of missense variants. Scores range from 0 to 1. The larger the score the more likely the SNP has damaging effect. "REVEL scores are freely available for non-commercial use. For other uses, please contact Weiva Sieh" (weiva.sieh@mssm.edu)`


# Long Description

REVEL is an ensemble method for predicting the pathogenicity of missense variants based on a combination of scores from 13 individual tools: MutPred, FATHMM v2.3, VEST 3.0, PolyPhen-2, SIFT, PROVEAN, MutationAssessor, MutationTaster, LRT, GERP++, SiPhy, phyloP, and phastCons.  REVEL was trained using recently discovered pathogenic and rare neutral missense variants, excluding those previously used to train its constituent tools.  The REVEL score for an individual missense variant can range from 0 to 1, with higher scores reflecting greater likelihood that the variant is disease-causing.  When applied to two independent test sets, REVEL had the best overall performance (p<10-12) compared with any individual tool and seven ensemble methods: MetaSVM, MetaLR, KGGSeq, Condel, CADD, DANN, and Eigen.  Importantly, REVEL also had the best performance for distinguishing pathogenic from rare neutral variants with allele frequencies <0.5%.  Compared with other ensemble methods, the area under the receiver operating characteristic curve (AUC) for REVEL was 0.046-0.182 higher in an independent test set of 935 recent SwissVar disease variants and 123,935 putatively neutral exome sequencing variants, and 0.027-0.143 higher in an independent test set of 1953 pathogenic and 2406 benign variants recently reported in ClinVar.  We provide precomputed REVEL scores for all possible human missense variants to facilitate the identification of pathogenic variants in the sea of rare variants discovered as sequencing studies expand in scale.

# Schema

[Figures](https://sites.google.com/site/revelgenomics/) 

# Exemple

# Source

[dbNSFP](https://sites.google.com/site/jpopgen/dbNSFP)

[Publication](https://linkinghub.elsevier.com/retrieve/pii/S0002929716303706)

[Site](https://sites.google.com/site/revelgenomics/))
