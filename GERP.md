# Name
-
GERP (Genomic Evolutionary Rate Profiling)

# Version
-
2011/05/22

# Usefull for
-
Conserved loci

# Short description
-
"GERP identifies constrained loci in multiple sequence alignments by comparing the level of substitution observed to that expected if there was no functional constraint."

# Orientation and range
-
* Positive scores represent highly-conserved positions while negative scores represent highly-variable positions.
* Scores range from -12.3 to 6.17.
* A score of 0 indicates that the alignment was too shallow at that position to get a meaningful estimate of constraint.
* In practice, we find that a RS score threshold of 2 provides high sensitivity while still strongly enriching for truly constrained sites. 
* the highest score of any base in a multi-base deletion is displayed.
* the mean of the scores of the two flanking bases is shown for an insertion.

# Methodology
-
Based on the maximum likelihood evolutionary rate estimation for position-specific scoring.
For each position of the multiple alignment we compute the conservation score in rejected substitutions bysubtracting the estimated evolutionary rate from the neutral rate. The neutral rate is computed by removing species gapped at that position from thephylogenetic tree and summing the branch lengths of the resulting projected tree; the evolutionary rate is estimated by computing the maximumlikelihood rescaling of the projected tree. (2) Given position-specific conservation scores, we generate a set of candidate elements. (3) For eachcandidate element, we compute a p-value to represent the likelihood of observing a segment of equal length and greater than or equal score underthe null model. We then select a non-overlapping set of elements in order of increasing p-value.

# VCF description (VEP)
-
`##GERP++_NR=(from dbNSFP) GERP++ neutral rate`
`##GERP++_RS=(from dbNSFP) GERP++ RS score, the larger the score, the more conserved the site. Scores range from -12.3 to 6.17.`
`##GERP++_RS_rankscore=(from dbNSFP) GERP++ RS scores were ranked among all GERP++ RS scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of GERP++ RS scores in dbNSFP.`

# Long Description
-
Genomic Evolutionary Rate Profiling (GERP) is a method for producing position-specific estimates of evolutionary constraint using maximum likelihood evolutionary rate estimation. It also discovers "constrained elements" where multiple positions combine to give a signal that is indicative of a putative functional element; this track shows the position-specific scores only, not the element predictions.
Constraint intensity at each individual alignment position is quantified in terms of a "rejected substitutions" (RS) score, defined as the number of substitutions expected under neutrality minus the number of substitutions "observed" at the position.
Sites are scored independently. Positive scores represent a substitution deficit (i.e., fewer substitutions than the average neutral site) and thus indicate that a site may be under evolutionary constraint. Negative scores indicate that a site is probably evolving neutrally; negative scores should not be interpreted as evidence of accelerated rates of evolution because of too many strong confounders, such as alignment uncertainty or rate variance. Positive scores scale with the level of constraint, such that the greater the score, the greater the level of evolutionary constraint inferred to be acting on that site.
GERP was applied to quantify the level of evolutionary constraint acting on each site in hg19, based on an alignment of 35 mammals to hg19 with a maximum phylogenetic scope of 6.18 substitutions per neutral site. Gaps in the alignment are treated as missing data, which means that the number of substitutions per neutral site will be less than 6.18 in sites where one or more species has a gap. Thus, RS scores range from a maximum of 6.18 down to a below-zero minimum, which we cap at -12.36. RS scores will vary with alignment depth and level of sequence conservation. 

# Example:
-
In TP53 we can see low GERP score (around 0) on the left which means that the loci aren’t really conserved so the substitutions observed in these locations should not be so much pathogenic. Whereas at the right we can see high score (around 5 for a maximum of 6.17) so these locations are much more conserved and the substistions in here should be much more damaging. The ClinVar interpretation is validating the observations so the GERP score is usefull.
https://genome.ucsc.edu/cgi-bin/hgTracks?db=hg19&lastVirtModeType=default&lastVirtModeExtraState=&virtModeType=default&virtMode=0&nonVirtPosition=&position=chr17%3A7576837%2D7576857&hgsid=1039105607_CnqTNBavTHS9mAqm5gSXzAsNT9s2
 
# Schema
-
[Figure 1](http://mendel.stanford.edu/SidowLab/pdfs/2010DavydovEtAl.pdf)

# Source/Publication/Tool
-
[Tool](http://mendel.stanford.edu/SidowLab/downloads/gerp/)
[Publication](http://mendel.stanford.edu/SidowLab/pdfs/2010DavydovEtAl.pdf)
