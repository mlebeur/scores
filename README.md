# scores

Description of scores used for genomic interpretation of variants.

List of scores:

Format:
* Name
* Version
* Type = {Score | Metascore}
* Category = {conservation | Functionnal | ... to define}
* Usefull for = {to define}
* Short description
* Orientation and range
* Methodology
* VCF description (VEP)
* Long Description
* Exemple
* Source


As some score are based on other scores the following array should ive a nice overview of their interactions:

| Metascores/scores | Number of annotations | GERP | phastCons | phyloP | Grantham | SIFT | PolyPhen | MutationTaster | MutationAssessor | FATHMM | LRT | SiPhy | 1000G AF | ESP AF | ClinVar | HGMD | gnomAD/BRAVO variant density | VEST | PROVEAN | MutPred | Gene Annotation? | bstatistic | mirSVR | targetScan | chromHMM | Encode expresion | Encode  nucleosome position | Encode  histone modification | Encode open chromatine | Encode DNAse hypersensitiv | Encode promoter-associated regulatory features | JASPAR | Segway | tOverlapMotifs | TFBS | mutationDensity | nearestMutation | dbscSNV | GC | CpG | NNSplice |
| - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
| CADD | 63 | X | X | X | X | X |  |  |  |  |  |  | X | X |  |  | X |  |  |  | X | X | X | X | X | X | X | X | X | X |  |  | X | X | X | X | X | X | X | X |  |
| MetaLR/SVM | 10 | X |  | X |  | X | X | X | X | X | X | X | X |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| REVEL | 13 | X | X | X |  | X | X | X | X | X | X | X |  |  |  |  |  | X | X | X |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| MutationTaster2 |  |  | X | X |  |  |  |  |  |  |  |  | X |  | X | X |  |  |  |  |  |  |  |  |  |  |  | X |  | X | X | X |  |  |  |  |  |  |  |  | X |

