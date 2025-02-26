# Enhancing Screening Methods for Bladder Cancer Detection using Data Augmentation and Genetic Algorithm Strategies

## Abstract

Bladder cancer is the most expensive of all cancers to diagnose, treat and monitor due to its
reliance on manual procedures in each of these phases. It is also highly invasive for the
patient. The main non-invasive screening method currently in use is urine cytology where a
pathologist reviews the structure of cells in urine samples for abnormalities. This process has
poor sensitivity and can result in unacceptable high levels of false negatives. Many
experimental techniques have been used to improve the diagnosis of bladder cancer from
urine samples and incorporate machine learning techniques to improve prediction accuracy
from structured tabular data. Most of the studies to date have utilised small samples sizes
and simple techniques for optimising their detection models and while some performances
have been outstanding their high variability in repeat experiments and/or unsuitability for
clinical implementation due to high equipment costs and need for specialist staff means they
cannot replace in-situ procedures. Another key issue with such experiments is that they tend
to use patient data from only one location/hospital and thus may not generalise well to new
patient data.

This study brings together two techniques which can improve generalisation and improve
performance of a bladder cancer detection model built on voided urine samples. A tuned
Generative Adversarial Network is used to create synthetic data samples to be augmented to
tabular training dataset and a genetic algorithm is employed to optimise the feature and
hyperparameter selections of a lightGBM classifier. The aim is to develop a model which
minimises the trade-off between false negatives and false positives when being used by a
clinician for decision making on patient risk and hence improving the area under the
precision-recall key is the key objective. A framework was developed which considers
different sizes of augmented training datasets, evaluates its fidelity and ensures that the
models are reliable for clinicians in terms of the extended training data maintaining the
underlying structure of the original data and the predicted probabilities for the models reflect
actual likelihoods (calibrated). 

## Summary of findings

The results of the experiments could not be proven to be statistically significant and hence
the null hypothesis cannot be rejected, that is, there is no significant difference between PRAUC for a BC detection model enhanced by the use of DA & GA strategies and one without.
The permutation test used to test the results however might not be robust given the small
number of samples being tested and so while the research question is answered negatively
the descriptive results show that it can be worthwhile employing the approach to other
studies on BC detection from urine samples where more data is available.

The descriptive statistics shows that there may be a positive monotonic relationship between
the size of synthetic dataset augmented to the training dataset, the fidelity of that synthetic
data and model performance. But it needs to be tested by considering more sizes of
augmentation. This finding, if statistically valid, differs from other studies which found in
most experiments the fidelity of synthetic data decreases as the number of samples
increases. However, GANs are notoriously sensitive to their hyperparameters settings and
these studies only ever utilised default values.

It is important in a medical setting that the data a model is built on can be trusted and this
means the fidelity of the synthetic data is sound and this study has concentrated on that
aspect. Some studies solely investigate the impact of the size of synthetic datasets on model
performance but this runs the risk of the synthetic data having artificial relationships
between features which are not representative of both the real data and the domain
knowledge on how different ion and enzymes relate to bladder cancer.

Another key aspect of this study has been to build a model which can reduce the trade-off
between false negatives and false positives and thus enable the user of the model to make
better decisions about patient risk. So a primary aim was to increase the PR-AUC and try to
minimise the levels of false negatives. All aspects of the model build utilised evaluation
function to take this into account whilst other studies focussed on accuracy. Also when
considering label assignments studies rarely detail how they obtain their threshold variant
performance metrics and so comparisons cannot be made easily. Also the need for models to
be calibrated is a required for cancer detection models to ensure they are reliable, and this
too is often overlooked in studies and hence their results could be falsely inflated. 
