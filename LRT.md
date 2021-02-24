# Name

LRT (Likelihood Ratio Test)

# Version

1

# Usefull for

Identified conserved amino acid.

# Short description

Using a comparative genomics data set of 32 vertebrate species we show that a likelihood ratio test (LRT) can accurately identify a subset of deleterious mutations that disrupt highly conserved amino acids within protein-coding sequences, which are likely to be unconditionally deleterious.

# Orientation and range

LRT score ranges from 0 to 1.

LRT prediction which is not solely determined by the score.

| Prediction |
| - |
| D(eleterious) |
| N(eutral) |
| U(nknown) |

The LRT converted rankscore, which is compute as LRTnew=1-LRTori*0.5 if Omega<1 or LRTnew=LRTori*0.5 if Omega>=1, ranges from 0.00162 to 0.84324.

The LRT Omega is the nonsynonymous-to-synonymous-rate ratio estimation.

# Methodology

## Comparative genomic data set

Multiple sequence alignments of protein-coding sequences were generated from 32 vertebrate species. Orthologous protein sequences were downloaded from Ensembl, originally inferred by TreeBest, aligned using MUSCLE, and then backtranslated into nucleotide alignments. All known selenocysteine residues were masked. After removing alignments with too few orthologous, <10 eutherian mammals, there were 18,993 alignments with an average of 16.5 species per alignment. 

## Likelihood ratio test (LRT)

The LRT was used to compare the null model that each codon is evolving neutrally, with no difference in the rate of nonsynonymous (dN) to synonymous (dS) substitution, to the alternative model that the codon has evolved under negative selection with a free parameter for the dN/dS ratio. 

To make the predictions of the LRT available to the community for every potential nonsynonymous variant in the human genome, we applied it to 10,073,284 codons for which there were a sufficient number of aligned species. A total of 5,828,045 sites were significant (P < 0.001 and dN/dS < 1).

# VCF description (VEP)

`##LRT_Omega=(from dbNSFP) estimated nonsynonymous-to-synonymous-rate ratio (Omega, reported by LRT)`

`##LRT_converted_rankscore=(from dbNSFP) LRTori scores were first converted as LRTnew=1-LRTori*0.5 if Omega<1, or LRTnew=LRTori*0.5 if Omega>=1. Then LRTnew scores were ranked among all LRTnew scores in dbNSFP. The rankscore is the ratio of the rank over the total number of the scores in dbNSFP. The scores range from 0.00162 to 0.84324.`

`##LRT_pred=(from dbNSFP) LRT prediction, D(eleterious), N(eutral) or U(nknown), which is not solely determined by the score.`

`##LRT_score=(from dbNSFP) The original LRT two-sided p-value (LRTori), ranges from 0 to 1.`

# Long Description

Using a comparative genomics data set of 32 vertebrate species we show that a likelihood ratio test (LRT) can accurately identify a subset of deleterious mutations that disrupt highly conserved amino acids within protein-coding sequences, which are likely to be unconditionally deleterious. The LRT is also able to identify known human disease alleles.

Using a likelihood ratio test (LRT) 796–837 amino acid as altering mutations per genome that disrupt highly conserved amino acids were identified.

# Training set

Deleterious mutations within three human genomes.

# Exemple

# Schema

# Source

[Site](http://www.genetics.wustl.edu/jflab/lrt_query.html)

[Publication](https://genome.cshlp.org/content/19/9/1553.abstract)
