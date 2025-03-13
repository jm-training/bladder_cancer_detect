## Enhancing Screening Methods for Bladder Cancer Detection using Data Augmentation and Genetic Algorithm Strategies


### Project objectives

1. Build a bladder cancer/non-cancer classification model from biochemical and urinalysis data from voided urine samples
2. Model outperforms current state-of-the-art models using the same data
3. Model generalizes better to new data than that of current State-of-the-Art (SoA) models
4. Model enables better decision making on patient risk by minimising the trade-off between false negatives and false positives produced by the model
5. Make recommendations on future research in cancer detection models from voided urine samples


### Analysis approach

1. Exploratory data analysis and data pre-processing on the raw medical dataset
   - cf. code '1. Data preprocessing.ipynb'
2. Build a Conditional Tabular Generative Adverserial Network (CTGAN) to produce set numbers of synthetic observations from the original dataset (25%, 50%, 100%, 250%, 500% and 1,000% of size of original dataset)
   - cf. code '2a. Data augmentation - CTGAN - Default hyperparameters.ipynb'
3. Repeat the (2) but for each augmentation scenario (e.g. 25%) optimise the GAN by selecting hyperparameters which maximise the fidelity score metrics of each synthetic dataset created (=evaluation function)
   - cf. code '2b. Data augmentation - CTGAN - Optimised hyperparameters.ipynb'
4. Use LGBM classifier to build predictive models for each augmented training dataset & evaluate on hold-out data
   - use RFE for best feature subset selection & random search for hyperparameter tuning
   - use custom PR-AUC function for all model performance evaluation on cross-validation folds and hold-out data datasets in line with project objective
   - calibrate probability scores using Platt scaling to ensure that the predicted probabilities reflect the true likelihood of the corresponding outcomes
   - evaluate models on the threshold invariant metrics of PR/ROC-AUC and hypothesis tests using permutation technique
   - cf. code '3a. Classification models - LGBM - Non-GA.ipynb'
6. Similar to (4) but use Genetic Algorithm (GA) search to optimize selections of features and LGBM hyperparameters
   - use Google GPUs to minimise processing time
   - cf. code '3b. Classification models - LGBM - GA'
7. Summary plots and tables on:
   - exploratory data analysis
   - CTGAN generator and discriminator performances
   - fidelity of synthetic data
   - performance of best models versus baseline model
   - feature importance
   - calibration analysis on best models
   - permutations testing on PR-AUCs of each model via hypothese tests
   - cf. '4a. Analysis summary 1' and '4b. Analysis summary 2'


### Results/findings

1. Descriptive statistics show that there is a positive monotonic relationship between the size of synthetic dataset augmented to the training dataset, the fidelity of that synthetic data and model performance difference between PR-AUC for a BC detection model enhanced by the use of DA & GA strategies and one without. But the results of the experiments could not be proven to be statistically significant and hence the null hypothesis cannot be rejected
2. The permutation test used to test the results however might not be robust given the small number of samples being tested and so while the research question is answered negatively the descriptive results show that it can be worthwhile employing the approach to other studies on BC detection from urine samples where more data is available
3. It is important in a medical setting that the data a model is built on can be trusted and this means the fidelity of the synthetic data is sound and this study has concentrated on that aspect. Some studies solely investigate the impact of the size of synthetic datasets on model performance but this runs the risk of the synthetic data having artificial relationships between features which are not representative of both the real data and the domain knowledge on how different ion and enzymes relate to bladder cancer
4. Another key aspect of this study has been to build a model which can reduce the trade-off between false negatives and false positives and thus enable the user of the model to make better decisions about patient risk. So a primary aim was to increase the PR-AUC and try to minimise the levels of false negatives. All aspects of the model build utilised evaluation function to take this into account whilst other studies focussed on accuracy. Also when 
considering label assignments studies rarely detail how they obtain their threshold variant performance metrics and so comparisons cannot be made easily. Also the need for models to be calibrated is a required for cancer detection models to ensure they are reliable, and this too is often overlooked in studies and hence their results could be falsely inflated
5. Performance comparisons with SOA models is difficult because of the points raised in (4)
