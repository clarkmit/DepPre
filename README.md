# ABCD Study Machine Learning Analysis Framework

This repository contains the code implementation for analyzing the Adolescent Brain Cognitive Development (ABCD) study data using advanced machine learning techniques.

Link for colab, [here](https://colab.research.google.com/drive/1lhAUNdN560OZEO--pxPPmu9PZG9NXlEt?usp=sharing)

## Overview

This framework provides comprehensive tools for:
- Predictive modeling of depression and related outcomes in adolescents
- Analysis of longitudinal data across multiple timepoints (T0-T4)
- Feature importance and interaction analysis
- Ensemble learning with multiple model architectures
- Extensive visualization and evaluation capabilities

## Key Features

- **Multiple Model Support**: 
  - CatBoost
  - Random Forest
  - XGBoost
  - TabPFN
  - Elastic Net
  - Stacking/Bagging Ensembles

- **Advanced Analysis Tools**:
  - SHAP (SHapley Additive exPlanations)
  - H-statistics for feature interactions - Optional
  - Conformal prediction - Optional
  - GAM (Generalized Additive Models) - Optional
  - Quantile analysis - Optional

- **Visualization Suite**:
  - Feature importance plots
  - Interaction matrices
  - SHAP summary plots
  - Performance metrics visualizations
  - Spider plots for cross-category comparison

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

1. Load your ABCD study data (format detailed in Data Format section)
2. Configure analysis parameters:
   ```python
   tp_option = '2'  # Timepoint selection
   target_options = "depress_D_p"  # Target variable
   split = "within_categories"  # Analysis approach
   ```
3. Run the analysis pipeline

## Data Format

Required data structure:
- Longitudinal data across timepoints (T0-T4)
- Features organized by categories (cognitive, behavioral, neuroimaging, etc.)
- Target variables for depression and related outcomes

## Citation

If you use this code in your research, please cite:

```bibtex
[PAPER CITATION]
```

## License

[LICENSE TYPE]

## Contributors

[LIST OF AUTHORS]

## Contact

For questions about the code, please open an issue or contact authors.
