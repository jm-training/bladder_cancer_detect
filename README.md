# Bladder cancer detection

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
