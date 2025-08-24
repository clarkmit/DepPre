# High-Dimensional Predictive Modelling using Ensemble Stacking Machine Learning Analysis Framework for Longitudinal ABCD Data 
This repository contains the code implementation for analyzing the Adolescent Brain Cognitive Development (ABCD) study data using a variety of advanced machine learning methods for predictive analysis using a vast high-dimensional variety of biopsychosocial variable types, and includes organized feature-engineering for all available timepoints of data acqusition.

Link to colab: https://colab.research.google.com/drive/1lhAUNdN560OZEO--pxPPmu9PZG9NXlEt#scrollTo=f5DW-i1ZWylJ

The colab should be run on a minimum of T4 GPU. If you were to run it locally, please ensure you have >= 10 GB of GPU RAM as TabPFN will take up your GPU RAM, and >= 10 GB System RAM for the feature combinations.

## Central Project Aim
Address the fundamental question: Which of a vast range of currently available biopsychosocial measurements best predict hallmark psychiatric outcomes? Feature-sets are organized both within and across an ontology of theory-driven, commonly used, or potentially informative categories (upon a rough biopsychosocial gradient) to assess both hierarchical and interactive predictive power.

## Organizational Procedures
Feature-set categories included over 1,000 unique Biological, Psychological, Social, and Environmental measurements across 5 available time points using data from ~23,760 children and adults/parents, including (but not limited to):
Biological: Neuroimaging (structural, DTI, resting-state, task-fMRI), ancestral genetic PCs, physiological fitbit data
Psychological: Experimental cognitive assessments (including hierarchical Bayesian modelling of individual trial-level behavior), personality traits, behavioral features, co-extensive individual and familial psychopathological dimensions, etc
Social: Parenting styles, family dynamics, quality/dynamics of peer relationships, socioeconomic factors
Environmental: Adverse life events, residential characteristics, cultural factors
Temporal: Delta calculations were generated for many variables with available time points which were theoretically relevant to psychopathology

## Predictive Targets:
Hallmark psychiatric features: depression, anxiety, ADHD, externalizing behaviors
Contrasting functional outcomes: social problems, cognitive task performance, academic performance
Multiple operationalizations: dimensional, categorical, recent onset of clinically relevant symptoms

## Overview
This framework provides comprehensive tools for:
- Predictive and comparitive modeling of hallmark psychiatric dimensions and categories in adolescents and adults
- Organized longitudinal data across multiple timepoints (T0-T4) with categorized feature-sets using available variables from each acqusition point
- Multiple High-Performance Model Ensemble learning architecture
- Outputs of feature importance for meta-models, individual ML models, and interaction analysis
- Extensive visualization and model evaluation capabilities

## Key Features in Analytic Pipeline
- **Multiple ML Models & Stacking Functions/Availability**: 
  - CatBoost
  - Random Forest
  - XGBoost
  - TabPFN
     - Stacking
     - Bagging - Optional
  - Additional simpler models used for validation 
  - Elastic Net
  - Ridge
  
- **Analysis Tools**:
  - SHAP (SHapley Additive exPlanations)
  - H-statistics for feature interactions - Optional
  - Conformal prediction - Optional
  - GAM (Generalized Additive Models) - Optional
  - Quantile analysis - Optional

- **Visualization Options**:
  - Feature importance plots
  - Interaction matrices
  - SHAP summary plots
  - Performance metrics visualizations
  - Spider plots for cross-category comparison
 
- **Additional Modelling Support**:
  - Built in pre-processing functions and imputation capabilities
  - Available variables organized for each available time point of data acqusition
  - Cross-Validation using K-Folds to prevent overfitting and provide nested validation
  - Handles mixed data types (continuous, categorical, ordinal)
  - Variables organized around missing data which were collected and assesed at different time points
  - Advanced interaction assesment, including additional metrics to adjust for model complexity and options to specify domain-specific categories for analysis
  - Additionally organized feature-sets arranged across a spectrum of objective to subjective measurements

## Requirements

```python
catboost>=1.2
xgboost>=1.7
sklearn>=1.0
shap>=0.41
tabpfn>=0.1
pygam>=0.9
mapie>=0.7
optuna>=3.0
```

## Installation

```bash
pip install -r requirements.txt
```

or just run the setting up cell in the colab.

## Usage

The main analysis pipeline is available in `ABCD_analysis.ipynb`. To use:

1. *** Use of ABCD study requires lisence 
2. Load ABCD study data (format detailed in Data Format section)
3. Configure analysis parameters:
   ```python
   tp_option = '2'  # Timepoint selection
   target_options = "depress_D_p"  # Target variable
   split = "within_categories"  # Analysis approach
   ```
   More guides on the params, [here](https://github.com/clarkmit/DepPre/blob/main/parameters_guide.md)
4. Run the analysis pipeline

## Data Format

Required data structure for full analysis:
- Longitudinal data across timepoints (T0-T4). Request can be made only if lisence acquired 
- Features organized by categories (cognitive, behavioral, neuroimaging, etc.)
- Target variables for depression and related outcomes



## Full Methodological Framework above was used as part of:
"Hierarchical, Interactive, and Dynamic Predictive Capacity of Current Biological, Psychological, Social, and Environmental Measurements in Depression, Anxiety, ADHD, and Social Quality across Lifespan"

  # Some Additional Synergistic Statistical Models & Analysis used in research article included:
  1. Autoregressive Cross-Lagged Panel Network (CLPN) Models
  Purpose: Further explore bidirectional relationships and potential developmental causal pathways between psychopathological dimensions over time
  Implementation: LASSO regression with 10-fold cross-validation
  Features:
  Autoregressive effects (temporal stability)
  Cross-lagged relationships (potential causality)
  Network centrality analysis (OutStrength, InStrength, Betweenness, Closeness)
  Bootstrap stability assessment (1000 iterations)
  
  2. Bayesian Mixed Models (BMM)
  Purpose: Examine relationships with enhanced interpretability and uncertainty quantification
  Synergistic Advantages:
  Robust handling of missing data
  Comprehensive uncertainty quantification through posterior distributions
  Population-level and individual-level variability modeling
  Random intercepts for subjects
  Implementation: 4 MCMC chains, 8,000 iterations (2,000 warmup)
  Validation: Rhat values (<1.01), effective sample sizes
  
  3. ANCOVA Models
  Purpose: Examine stratified effects of factors
  Post-hoc: Tukey's tests with Bonferroni correction



## Contributors
Clark Roberts, Zhafira Fawnia 

## Contact
For questions about the code, please contact authors and note that access to data requires lisence.
