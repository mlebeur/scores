# scores

Description of scores used for genomic interpretation of variants.

List of scores:

Format:
* Name
* Version
* Type = {Score | Metascore}
* Category = {Conservation | Functionnal}
* Usefull for = {to define}
* Short description
* Orientation and range
* Methodology
* VCF description (VEP)
* Long Description
* Exemple
* Source


As some score are based on other scores the following array should ive a nice overview of their interactions:

| Metascores/scores | Number of annotations | [GERP](GERP.md) | [phastCons](phyloP_PhasCons.md) | [phyloP](phyloP_PhasCons.md) | Grantham | [SIFT](SIFT.md) | [PolyPhen](polyphen2.md) | [MutationTaster](MutationTaster.md) | [MutationAssessor](MutationAssessor.md) | [FATHMM](FATHMM.md) | [LRT](LRT.md) | [SiPhy](SiPhy.md) | 1000G AF | ESP AF | ClinVar | HGMD | gnomAD/BRAVO variant density | [VEST](VEST.md) | [PROVEAN](PROVEAN.md) | [MutPred](MutPred.md) | Gene Annotation? | bstatistic | mirSVR | targetScan | chromHMM | Encode expresion | Encode  nucleosome position | Encode  histone modification | Encode open chromatine | Encode DNAse hypersensitiv | Encode promoter-associated regulatory features | JASPAR | Segway | tOverlapMotifs | TFBS | mutationDensity | nearestMutation | dbscSNV | GC | CpG | NNSplice |
| - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| [DANN](DANN.md) | 63 | X | X | X | X | X |  |  |  |  |  |  | X | X |  |  | X |  |  |  | X | X | X | X | X | X | X | X | X | X |  |  | X | X | X | X | X | X | X | X |  |
| [CADD](CADD.md) | 63 | X | X | X | X | X |  |  |  |  |  |  | X | X |  |  | X |  |  |  | X | X | X | X | X | X | X | X | X | X |  |  | X | X | X | X | X | X | X | X |  |
| [MetaLR/SVM](Meta.md) | 10 | X |  | X |  | X | X | X | X | X | X | X | X |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| [REVEL](REVEL.md) | 13 | X | X | X |  | X | X | X | X | X | X | X |  |  |  |  |  | X | X | X |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| MutationTaster2 |  |  | X | X |  |  |  |  |  |  |  |  | X |  | X | X |  |  |  |  |  |  |  |  |  |  |  | X |  | X | X | X |  |  |  |  |  |  |  |  | X |
| [VEST](VEST.md) | 2 |  |   |   |  |  |  |  |  |  |  |  |  | X |  | X |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


An array resume of [Performance evaluation of pathogenicity-computation methods for missense variants](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6125674/)

<a href="https://github.com/mlebeur/scores/blob/main/Tools%20summary.pdf">Tools resume</a>

<> [Source S10](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6125674/)

<>[Source S10](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6125674/)

Some scores are more or less correlated as we can see on :

* the Meta publication dataset :  

![Meta sores correlation plot](Meta_correlation_plot.png)

* the Eigen publication dataset :  

![Eigen scores corelation plot](Eigen_correlation_plot_scores.png)

<a href="https://github.com/mlebeur/scores/blob/main/Supplementary%20Figure%20S10%20Spearman%20rank%20correlation%20coefficient%20based%20on%20three%20benchmark%20datasets.pdf">Another tool correlation</a>
