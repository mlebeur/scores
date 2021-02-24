# Name

FATHMM (Functional Analysis Through Hidden Markov Models)

# Version

v2.3

# Usefull for

Functionnal effect

# Short description

Predicting the functional effects of protein missense mutations by combining sequence conservation within hidden Markov models (HMMs), representing the alignment of homologous sequences and conserved protein domains, with "pathogenicity weights", representing the overall tolerance of the protein/domain to mutations. 

# Orientation and range

FATHMM score range from -16.13 to 10.64.

FATHMM rankscore, whixh is computed as FATHMMnew=1-(FATHMMori+16.13)/26.77, scores range from 0 to 1.

| FATHMM pred | FATHMM score | FATHMM rankscore |
| - | - | - |
| D(AMAGING) | <= -1.5 | >= 0.81332 |
| T(OLERATED) | >= -1.5 | <= 0.81332 |

Fathmm MKL coding score ranges from 0 to 1.

| MKL coding pred | fathmm-MKL_coding_score | Fathmm MKL coding rankscore |
| - | - | - |
| D(AMAGING) | > 0.5 | > 0.28317 |
| N(EUTRAL) | < 0.5 | < 0.28317 |

MKL_coding_group

# Methodology

The procedure for predicting the functional consequences on the protein function is as follows : the JackHMMER component of HMMER3 (one iteration with the optional –hand parameter applied) is used to search for homologous sequences within the UniRef90 database . As part of this procedure, an ab initio HMM representing the MSA of homologous sequences (with Dirichlet mixtures) is constructed and used. In conjunction, protein domain annotations from the SUPERFAMILY and Pfam databases are made. The relevant SUPERFAMILY and Pfam HMMs are then extracted only if and when the domain assignment is deemed significant (e-value ≤0.01) and the AAS maps onto a match state within the model.

The information gain (as measured by the Kullback–Leibler divergence from the SwissProt/TrEMBL amino acid composition) is then calculated at the corresponding match states within the HMMs extracted above. Next, we interrogate the underlying amino acid probabilities modeled by the most informative HMM and assume that a reduction in the amino acid probabilities (when comparing the wild-type to the mutant residue) indicates a potentially negative impact upon protein function whereas a gain in the amino acid probabilities indicates a more favorable substitution. Furthermore, we assume that larger reductions in amino acid probabilities have more substantial effects than smaller reductions in amino acid probabilities. Then Pw and Pm representing respectively the underlying probabilities for the wild-type and mutant amino acid residues are computed.

Then these measures are weighted by the relative frequency of disease-associated (HGMD) and functionally neutral (UniProt) AASs mapping onto the relevant SUPERFAMILY/Pfam HMM.

# VCF description (VEP)

`##fathmm-MKL_coding_group=(from dbNSFP) the groups of features (labeled A-J) used to obtained the score. More details can be found in doi: 10.1093/bioinformatics/btv009.`

`##fathmm-MKL_coding_pred=(from dbNSFP) If a fathmm-MKL_coding_score is >0.5 (or rankscore >0.28317) the corresponding nsSNV is predicted as "D(AMAGING)"; otherwise it is predicted as "N(EUTRAL)".`

`##fathmm-MKL_coding_rankscore=(from dbNSFP) fathmm-MKL coding scores were ranked among all fathmm-MKL coding scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of fathmm-MKL coding scores in dbNSFP.`

`##fathmm-MKL_coding_score=(from dbNSFP) fathmm-MKL p-values. Scores range from 0 to 1. SNVs with scores >0.5 are predicted to be deleterious, and those <0.5 are predicted to be neutral or benign. Scores close to 0 or 1 are with the highest-confidence. Coding scores are trained using 10 groups of features. More details of the score can be found in doi: 10.1093/bioinformatics/btv009.`

`##FATHMM_converted_rankscore=(from dbNSFP) FATHMMori scores were first converted to FATHMMnew=1-(FATHMMori+16.13)/26.77, then ranked among all FATHMMnew scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of FATHMMnew scores in dbNSFP. If there are multiple scores, only the most damaging (largest) rankscore is presented. The scores range from 0 to 1.`

`##FATHMM_pred=(from dbNSFP) If a FATHMMori score is <=-1.5 (or rankscore >=0.81332) the corresponding nsSNV is predicted as "D(AMAGING)"; otherwise it is predicted as "T(OLERATED)". Multiple predictions separated by ";", corresponding to Ensembl_proteinid.`

`##FATHMM_score=(from dbNSFP) FATHMM default score (weighted for human inherited-disease mutations with Disease Ontology) (FATHMMori). Scores range from -16.13 to 10.64. The smaller the score the more likely the SNP has damaging effect. Multiple scores separated by ";", corresponding to Ensembl_proteinid.`

# Long Description

FATHMM is comprised of two algorithms: one sequence/conservation based (unweighted) and the other combines sequence conservation with pathogenicity weights (weighted). In short, our weighted algorithm is capable of adjusting our conservation-based predictions to account for the tolerance of related sequences to mutations.

# Exemple

[Site](http://fathmm.biocompute.org.uk/inherited.html)

# Schema

[Supplementary material 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3558800/)

# Source

[Publication](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3558800/)

[FATHMM](http://fathmm.biocompute.org.uk)

[fathmm-MKL](http://fathmm.biocompute.org.uk/fathmmMKL.htm)

[fathmm-XF](http://fathmm.biocompute.org.uk/fathmm-xf/)
