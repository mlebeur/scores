# Name

DANN (Deleterious Annotation of genetic variants using Neural Networks)

# Version

1

# Usefull for

Pathogenicity

# Short description

DANN score whole-genome variants by training a deep neural network (DNN).

# Orientation and range

DANN score ranges from 0 to 1.

A larger number indicate a higher probability to be damaging.

# Methodology

## Model training

DANN trains a DNN consisting of an input layer, a sigmoid function output layer, and three 1000-node hidden layers with hyperbolic tangent activation function. We use deepnet (https://github.com/nitishsrivastava/deepnet) to exploit fast Compute Unified Device Architecture (CUDA) parallelized GPU programming on an NVIDIA Tesla M2090 card and applied dropout and momentum training to minimize the cross entropy loss function. Dropout reduces over-fitting by randomly dropping nodes from the DNN (Srivastava, 2013). Momentum training adjusts the parameter increment as a function of the gradient and learning rate (Sutskever et al., 2013). DANN uses a hidden node dropout rate of 0.1, a momentum rate that increases from 0.01 to 0.99 linearly for the first 10 epochs and then remains at 0.99, and stochastic gradient descent (SGD) with a minibatch size of 100. As a baseline comparison, we trained a LR model. For LR training, we applied SGD using the scikit-learn library (Pedregosa et al., 2011) with parameter α = 0.01, which we found to maximize the accuracy of the LR model. LR and DNN are sensitive to feature scaling, so we preprocess the features to have unit variance before training either model. We also train an SVM using the LIBOCAS v0.97 library (Franc and Sonnenburg, 2009) with parameter C = 0.0025, closely replicating CADD’s training.

## Features

There are a total of 949 features defined for each variant. The feature set is sparse, and includes a mix of real valued numbers, integers, and binary values. For example, amino acid identities are only defined for coding variants. To account for this, we include Boolean features that indicate whether a given feature is undefined, and missing values are imputed. Moreover, all n-level categorical values, such as reference allele identity, are converted to n individual Boolean flags. See the Supplementary of Kircher et al. (2014) for more details about the features and imputation.

# VCF description (VEP)

`##DANN_rankscore=(from dbNSFP) DANN scores were ranked among all DANN scores in dbNSFP. The rankscore is the ratio of the rank of the score over the total number of DANN scores in dbNSFP.`

`##DANN_score=(from dbNSFP) DANN is a functional prediction score retrained based on the training data of CADD using deep neural network. Scores range from 0 to 1. A larger number indicate a higher probability to be damaging. More information of this score can be found in doi: 10.1093/bioinformatics/btu703. For commercial application of DANN, please contact Daniel Quang (dxquang@uci.edu)`

# Long Description

# Exemple

# Warning

DANN is the evolution of CADD but using DNN in place of CADD SVN to tackle non linear representations of the data.

# Source

https://cbcl.ics.uci.edu/public_data/DANN/

https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4341060/
