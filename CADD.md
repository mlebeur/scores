Name

CADD (The Combined Annotation Dependent Depletion)

Version
1.5

# Usefull for

Pathogenicty / Functionnal impact / Regulating / Epigenetic

# Short description

CADD is a tool for scoring the deleteriousness of single nucleotide variants as well as insertion/deletions variants in the human genome. 

# Orientation and range

* The larger the score the more likely the SNP has damaging effect.
* ‘Raw’ scores are the immediate output from the machine learning model. They summarize the extent to which the variant is likely to have derived from the proxy-neutral (negative values) or proxy-deleterious (positive values) class.
* ‘PHRED-scaled’ scores are normalized to all potential 9 billion SNVs, and thereby provide an externally comparable unit for analysis. From 1 to 99.
* In VEP transcript with ‘PHRED-scaled’ scores above 30 appear as 'likely deleterious' and scores below as 'likely benign'.
* Variants with scores over 30 are predicted to be the 0.1% most deleterious possible substitutions in the human genome.

# Methodology:

Fixed or nearly fixed recent evolutionary changes were identified as differences between 1000 Genomes and the Ensembl Compara inferred human-chimpanzee ancestral genome (derived allele frequency (DAF) of at least 95%, 14.9 million SNVs and 1.7 million indels). To simulate an equivalent number of mutations, we used an empirical model of sequence evolution with CpG dinucleotide-specific rates and mutation rates locally scaled in megabase windows. For annotation, we used the Ensembl Variant Effect Predictor (VEP), data from the ENCODE project and information from UCSC genome browser tracks. These annotations span a wide range of data types including conservation metrics like GERP, phastCons, and phyloP; functional genomic data like DNase hypersensitivity and transcription factor binding; transcript information like distance to exon-intron boundaries or expression levels in commonly studied cell lines; and protein-level scores like Grantham, SIFT, and PolyPhen.

In CADD v1.0 (major release), the resulting variant-by-annotation matrix contained 29.4 million variants (half observed, half simulated) and [63 distinct annotations](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/nar/47/D1/10.1093_nar_gky1016/1/gky1016_supplemental_files.pdf?Expires=1616678019&Signature=LwgI9cWmkUB6EVz6U8UzQzIl7p2Xp2XvD3JGKIkPlQCj5~bMqVyAr7O1BMU9saebZEP45HzEzbO0WfZHUXDzHI9Rp0LNB-yv~m0QGU~QxUPp9LVbhIpyqoyYkZ68~KnBgutMk9AbsChawEept-zt0q5Oxd7zjIjbp7ye2my8amJKg2Q3osAcJy0-NncC-nWQdfqvOeTvXv3G24~D8fewmnebYckqimEhOnd4EHD-YhJg6MdH63pRO~lIOoXh2bSTvR-Pugwqs6Cy7qbRW7u3skduhPIIRQiEG3X00ZUpknGyGZ-qlJhmONKuWRjDFk4gsAeqis3jHFTHqTho~nOLNA__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA). We trained a support vector machine (SVM) with a linear kernel on features derived from these annotations, supplemented by a limited number of interaction terms. The same 63 annotations were obtained for all 8.6 billion possible substitutions in the human reference genome (GRCh37), and, after training on observed and simulated variants, the model was applied to score all possible substitutions. As the scale of the combined SVM score ("C-scores") is effectively arbitrary due to the annotations used, we defined phred-like scores ("scaled C-scores") ranging from 1 to 99, based on the rank of each variant relative to all possible 8.6 billion substitutions in the human reference genome. 

# VCF description (VEP)

`##CADD_phred=(from dbNSFP) CADD phred-like score. This is phred-like rank score based on whole genome CADD raw scores. Please refer to Kircher et al. (2014) Nature Genetics 46(3):310-5 for details. The larger the score the more likely the SNP has damaging effect. Please note the following copyright statement for CADD: "CADD scores (http://cadd.gs.washington.edu/) are Copyright 2013 University of Washington and Hudson-Alpha Institute for Biotechnology (all rights reserved) but are freely available for all academic, non-commercial applications. For commercial licensing information contact Jennifer McCullar (mccullaj@uw.edu)."`

`##CADD_raw=(from dbNSFP) CADD raw score for functional prediction of a SNP. Please refer to Kircher et al. (2014) Nature Genetics 46(3):310-5 for details. The larger the score the more likely the SNP has damaging effect. Scores range from -7.535037 to 35.788538 in dbNSFP. Please note the following copyright statement for CADD: "CADD scores (http://cadd.gs.washington.edu/) are Copyright 2013 University of Washington and Hudson-Alpha Institute for Biotechnology (all rights reserved) but are freely available for all academic, non-commercial applications. For commercial licensing information contact Jennifer McCullar (mccullaj@uw.edu)."`

`##CADD_raw_rankscore=(from dbNSFP) CADD raw scores were ranked among all CADD raw scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of CADD raw scores in dbNSFP. Please note the following copyright statement for CADD: "CADD scores (http://cadd.gs.washington.edu/) are Copyright 2013 University of Washington and Hudson-Alpha Institute for Biotechnology (all rights reserved) but are freely available for all academic, non-commercial applications. For commercial licensing information contact Jennifer McCullar (mccullaj@uw.edu)."`

# Long Description

While many variant annotation and scoring tools are around, most annotations tend to exploit a single information type (e.g. conservation) and/or are restricted in scope (e.g. to missense changes). Thus, a broadly applicable metric that objectively weights and integrates diverse information is needed. Combined Annotation Dependent Depletion (CADD) is a framework that integrates multiple annotations into one metric by contrasting variants that survived natural selection with simulated mutations.

C-scores strongly correlate with allelic diversity, pathogenicity of both coding and non-coding variants, and experimentally measured regulatory effects, and also highly rank causal variants within individual genome sequences. Finally, C-scores of complex trait-associated variants from genome-wide association studies (GWAS) are significantly higher than matched controls and correlate with study sample size, likely reflecting the increased accuracy of larger GWAS.

CADD can quantitatively prioritize functional, deleterious, and disease causal variants across a wide range of functional categories, effect sizes and genetic architectures and can be used prioritize causal variation in both research and clinical settings. 

# Example

A scaled score of 10 or greater indicates a raw score in the top 10% of all possible reference genome SNVs, and a score of 20 or greater indicates a raw score in the top 1%, regardless of the details of the annotation set, model parameters, etc.

# Schema

[Figure 1](https://academic.oup.com/nar/article/47/D1/D886/5146191)

# Warnings

The bottom 90% (7.7 billion) of all GRCh37/hg19 reference SNVs (8.6 billion) are compressed into scaled CADD units of 0 to 10. While the next 9% (top 10% to top 1%, spanning 774 million SNVs) occupy CADD-10 to CADD-20...

As a result, many variants that have substantively different raw scores may have very similar, or even the same, scaled scores; and scaled scores accurately resolve differences between variants’ scores only at the extreme top end.

Thus, when comparing distributions of scores between groups of variants (e.g. variants seen in cases versus variants seen in controls), raw scores should be used. However, when discovering causal variants or fine-mapping variants within associated loci, scaled scores are advantageous as they allow the user a direct interpretation in terms of the estimated pathogenicity relative to all possible SNVs in the reference genome.

# Source:

[Publication](https://academic.oup.com/nar/article/47/D1/D886/5146191)

[Tool](https://cadd.gs.washington.edu/)
