# Name

phyloP (phylogenetic P-values) and PhastCons (Phylogenetic Analysis with Space/Time Models Scores)

# Version

1

# Usefull for

Conservation

# Short description

phyloP and PhastCons scores measure evolutionary conservation at individual alignment sites. Interpretations of the scores are compared to the evolution that is expected under neutral drift. 

phastCons: Conservation scoring and identification of conserved elements.

phyloP: Computation of p-values for conservation or acceleration, either lineage-specific or across all branches.

# Orientation and range

phastCons 100way/20way vertebrate/mammalian score are based on the multiple alignments of 100/20 vertebrate/mammalian genomes (including human).

The larger the score, the more conserved the site. 

The scores range from 0 to 1.

phyloP 100way/20way vertebrate/mammalian are based on the multiple alignments of 100/20 vertebrate/mammalian genomes (including human).

The larger the pvalue, the more conserved the site. 

The scores range from -20.0 to 10.003 and from -13.282 to 1.199 for respectively 100way vertebrate and 20way mammalian.

The rankscores range from 0 to 1.

# Methodology

# VCF description (VEP)

`##phyloP100way_vertebrate=(from dbNSFP) phyloP (phylogenetic p-values) conservation score based on the multiple alignments of 100 vertebrate genomes (including human). The larger the score, the more conserved the site. Scores range from -20.0 to 10.003 in dbNSFP.`

`##phyloP100way_vertebrate_rankscore=(from dbNSFP) phyloP100way_vertebrate scores were ranked among all phyloP100way_vertebrate scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of phyloP100way_vertebrate scores in dbNSFP.`

`##phastCons100way_vertebrate=(from dbNSFP) phastCons conservation score based on the multiple alignments of 100 vertebrate genomes (including human). The larger the score, the more conserved the site. Scores range from 0 to 1.`

`##phastCons100way_vertebrate_rankscore=(from dbNSFP) phastCons100way_vertebrate scores were ranked among all phastCons100way_vertebrate scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of phastCons100way_vertebrate scores in dbNSFP.`

`##phyloP20way_mammalian=(from dbNSFP) phyloP (phylogenetic p-values) conservation score based on the multiple alignments of 20 mammalian genomes (including human). The larger the score, the more conserved the site. Scores range from -13.282 to 1.199 in dbNSFP.`

`##phyloP20way_mammalian_rankscore=(from dbNSFP) phyloP20way_mammalian scores were ranked among all phyloP20way_mammalian scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of phyloP20way_mammalian scores in dbNSFP.`

`##phastCons20way_mammalian=(from dbNSFP) phastCons conservation score based on the multiple alignments of 20 mammalian genomes (including human). The larger the score, the more conserved the site. Scores range from 0 to 1.`

`##phastCons20way_mammalian_rankscore=(from dbNSFP) phastCons20way_mammalian scores were ranked among all phastCons20way_mammalian scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of phastCons20way_mammalian scores in dbNSFP.`


# Long Description

## Likelihood ratio tests

The LRTs are based on the test statistic An external file that holds a picture, illustration, etc. Object name is 110inf2.jpg, where An external file that holds a picture, illustration, etc. Object name is 110inf3.jpg and An external file that holds a picture, illustration, etc. Object name is 110inf4.jpg are the maximum likelihood estimates of the parameter vectors associated with the null and alternative hypotheses, respectively. These estimates are obtained numerically, as described below. For our two-sided tests, the regularity conditions required for T to have an asymptotic χ12 null distribution hold. For our one-sided tests, however, the null hypothesis is at the boundary of the parameter space under the alternative hypothesis, which causes the asymptotic distribution to become a 50:50 mixture of a χ12 distribution and a point mass at zero (Self and Liang 1987). With both one-sided and two-sided tests, the asymptotic distributions are used to compute approximate P-values. Additional details are in Supplemental section S2.2.

The LRT-based scores used in the analysis of the ENCODE regions and in the conservation tracks are computed as − log10 P, where P is a two-sided P-value. In order to distinguish conservation and acceleration scores, the scores are negated if the estimated ρ (or λ) suggest faster-than-neutral evolution (Supplemental section S2.2). This scoring system is produced by running phyloP with the option --mode CONACC.

## Score tests

The score tests are based on test statistics of the form An external file that holds a picture, illustration, etc. Object name is 110inf5.jpg, where U is the score function (the vector of partial derivatives of the log likelihood) and I is the Fisher information matrix. Both U and I are defined with respect to θ1 but evaluated at the maximum-likelihood estimate under the null hypothesis, An external file that holds a picture, illustration, etc. Object name is 110inf6.jpg. S is known, like T above, to have an asymptotic χj2 null distribution, where j is the difference in the number of free parameters of θ0 and θ1 (j = 1 here), and this asymptotic distribution is used by phyloP in computing P-values. Notably, the score test has the same local power as the LRT, being a most powerful test for small deviations from the null hypothesis (in this case, weak conservation or acceleration). However, the score test requires fitting only the null model to the data, instead of both the null and alternative models, which results in a substantial savings in computation. Indeed, with our all-branch test, no estimation is required because the null model has no free parameters. The subtree case requires estimation of a single scale factor ρ to fit the null model to the data. For both types of tests, computation of the Fisher information matrix appears to be intractable, so we approximate it by Monte Carlo sampling. Additional details are in Supplemental section S2.3.

## SPH tests

The all-branch SPH test is based on a test statistic (denoted n) equal to the number of substitutions that have occurred along the branches of a phylogeny in an alignment X, assuming a given neutral model ψ (Siepel et al. 2006). The exact null distribution of this statistic, An external file that holds a picture, illustration, etc. Object name is 110inf7.jpg, can be approximated arbitrarily closely by a uniformization procedure and a recursive dynamic programming algorithm that resembles Felsenstein's “pruning” algorithm. A closely related algorithm can be used to compute an estimate of n for an observed alignment X, and this estimate can be compared to the null distribution to compute a P-value. In the case of subtree tests, a similar procedure is used, but the joint distribution for the number of substitutions in a subtree of interest and the rest of the tree is considered (Siepel et al. 2006; Supplemental section S2.4). For various reasons, the P-values computed by this procedure tend to be somewhat conservative (Supplemental Fig. S4).

## GERP-like tests

GERP makes use of a statistic called “rejected substitutions” (RS), which is defined as the number of substitutions expected under a neutral model minus the number “observed” (estimated) for a particular alignment X (Cooper et al. 2005)—that is, the expected number of mutations that would have been fixed under neutrality but instead were “rejected” by purifying selection. For a given neutral model ψN and alignment X, GERP estimates a scaling parameter ρ for ψN by maximum likelihood (as in the LRT and SCORE tests), and estimates RS as An external file that holds a picture, illustration, etc. Object name is 110inf8.jpg, where T is the total branch length of the neutral model and An external file that holds a picture, illustration, etc. Object name is 110inf9.jpg is the estimated scale factor. While the other test statistics considered are conservative in the presence of missing data, RS can be quite sensitive to it, because a branch of length t for which no data are available will still contribute An external file that holds a picture, illustration, etc. Object name is 110inf10.jpg to the overall value of the test statistic. Therefore, a separate value of T is computed for each alignment X, by considering just the branches of the phylogeny for which aligned nucleotides are available. In addition, RS is set to zero if bases are available for fewer than three species. The GERP program (http://mendel.stanford.edu/sidowlab/downloads/gerp) assumes the use of the HKY85 substitution model and combines the steps of estimating the neutral substitution model and computing the desired RS values. To facilitate comparisons with the other tests, we reimplemented the core functionality of GERP within phyloP, treating it as analogous to the other all-branch tests in all respects. (It is not supported for subtree tests.) Like the GERP program, phyloP simply outputs the raw RS values and allows P-values to be computed separately in post-processing, if desired. To generate the ROC curves, we applied varying thresholds to RS for one-sided tests of conservation, to −RS for one-sided tests of acceleration, and to |RS| for two-sided tests. A comparison of phyloP's GERP mode with the latest version of GERP (version 2.1b) showed that the two programs were very similar in performance (Supplemental section S3.1).

# Example

[phastCons Tutorial](http://compgen.cshl.edu/phast/phastCons-tutorial.php)

[phyloP Tutorial](http://compgen.cshl.edu/phast/phyloP-tutorial.php)

# Schema

# Source

UCSC

[Phylop](https://ccg.epfl.ch/mga/hg19/phylop/phylop.html)

[PHAST](http://compgen.cshl.edu/phast/)

[Publication](https://pubmed.ncbi.nlm.nih.gov/19858363/)
