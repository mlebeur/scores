# Name

MutPred

# Version

v1.2

# Usefull for

Pahogenicity

# Short description

MutPred is a web application tool developed to classify an amino acid substitution as disease-associated or neutral in human. In addition, it predicts molecular cause of disease.

# Orientation and range

MutPred_score ranges from 0 to 1.

The larger the score the more likely the SNP has damaging effect.

| MutPred_score | pvalue | flag |
| - | - | - | 
| > 0.5 | < 0.05 | actionable hypotheses |
| > 0.75 | < 0.05 | confident hypotheses |
| > 0.75 | p < 0.01 | very confident hypotheses |

MutPred_rankscore ranges from 0 to 1.


# Methodology

A collection of five data sets of human amino acid substitutions were constructed from online databases and the literature (Cancer, Kinase, Hgmd, SPd and SPp).

A broad array of attributes from protein sequences were generated and used for classifcation.

These attributes can be grouped into three classes: (i) attributes based on predicted protein structure and dynamics, (ii) attributes based on predicted functional properties and (iii) attributes based on amino acid sequence and evolutionary information.

Sequence-based predictions of structural features or protein dynamics included secondary structure (Rost, 1996), solvent accessibility (Rost, 1996), transmembrane helices (Krogh et al., 2001), coiled-coil structure (Delorenzi and Speed, 2002), stability (Capriotti et al., 2005), B-factor (Radivojac et al., 2004), and intrinsic disorder (Peng et al., 2006). Predictions of functional sites included DNA-binding residues (Ahmad et al., 2004), catalytic residues (Xin and Radivojac, unpublished data), calmodulin-binding targets (Radivojac et al., 2006), as well as the phosphorylation (Iakoucheva et al., 2004), methylation (Daily et al., 2005), ubiquitination (Radivojac et al., 2009) and glycosylation (Radivojac, unpublished data) sites. Note that the calmodulin-binding target classifier predicts short structured or loosely structured helical segments within otherwise disordered regions and was used as a substitute for predicting Molecular Recognition Fragments (MoRFs), as proposed by Mohan et al. (2006). Each predictor, with the exception of N-linked glycosylation, was constructed in a supervised learning scenario, whereas the changes of N-linked glycosylation were modeled by simply counting whether a binding motif NX[ST] had been introduced or removed by the amino acid substitution (all structural and functional properties are listed in Table 2). Evolutionary attributes were generated from PSI-BLAST and also included a SIFT score, Pfam profile score (Finn et al., 2008), and transition frequencies. The transition frequencies, as proposed by Bromberg and Rost (2007), measure the likelihood of observing a given mutation in the UniRef80 database and Protein Data Bank

To discriminate between disease-associated mutations and neutral polymorphisms a random forest or a SVM were used.


# VCF description (VEP)

`##MutPred_AAchange=(from dbNSFP) Amino acid change used for MutPred_score calculation.`

`##MutPred_Top5features=(from dbNSFP) Top 5 features (molecular mechanisms of disease) as predicted by MutPred with p values. MutPred_score > 0.5 and p < 0.05 are referred to as actionable hypotheses. MutPred_score > 0.75 and p < 0.05 are referred to as confident hypotheses. MutPred_score > 0.75 and p < 0.01 are referred to as very confident hypotheses.`

`##MutPred_protID=(from dbNSFP) UniProt accession or Ensembl transcript ID used for MutPred_score calculation.`

`##MutPred_rankscore=(from dbNSFP) MutPred scores were ranked among all MutPred scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of MutPred scores in dbNSFP.`

`##MutPred_score=(from dbNSFP) General MutPred score. Scores range from 0 to 1. The larger the score the more likely the SNP has damaging effect.`

# Long Description

MutPred is based upon protein sequence, and which models changes of structural features and functional sites between wild-type and mutant sequences. These changes, expressed as probabilities of gain or loss of structure and function, can provide insight into the specific molecular mechanism responsible for the disease state. 

# Training set

| Data set | Substitutions | Proteins | Type | 
| - | - | - | - | 
| Cancer | 653 | 519 | Disease, somatic | 
| Kinase | 422 | 231 | Disease, somatic | 
| Hgmd | 26 655 | 1305 | Disease, inherited | 
| SPd | 6606 | 680 | Disease, inherited | 
| SPp | 23 426 | 8728 | Neutral, inherited | 

# Exemple

# Schema

# Source

[Publication](https://academic.oup.com/bioinformatics/article/25/21/2744/227925)
