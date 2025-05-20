# ABCD Study Analysis Parameters Guide

## Primary Parameters

### Time Point Selection (`tp_option`)
- **Values**: "0", "1", "2", "3", "4"
- **Purpose**: Selects the ABCD study timepoint for analysis
- **Details**:
  - T0: Baseline
  - T1: 6-month follow-up
  - T2: 1-year follow-up
  - T3: 18-month follow-up
  - T4: 2-year follow-up

### Group Selection (`group`)
- **Values**: "high_ale", "high_ale_severe_p_mh", "low_ale", "Female", "Male", "None"
- **Purpose**: Filters data for specific subgroup analysis
- **Details**:
  - high_ale: High adverse life events group
  - high_ale_severe_p_mh: High adverse life events with severe parent mental health
  - low_ale: Low adverse life events group
  - Female/Male: Gender-specific analysis
  - None: Full sample analysis

### Target Variable (`target_options`)
Key outcome variables including:
- **Depression Measures**:
  - "depress_D_p": Parent-reported depression
  - "depress_D_p_rev": Revised parent-reported depression
  - "dep_onset_rci_1.96"/"2.3": Depression onset with different RCI thresholds
  - "dep_remission_rci_1.96"/"2.3": Depression remission
  - "latent_class_depression": Latent class depression categorization

- **Cognitive Measures**:
  - "tb_fluid": Fluid intelligence
  - "tb_cryst": Crystallized intelligence
  - "tb_reading": Reading ability

### Analysis Split (`split`)
- **Values**: "across_categories", "within_categories"
- **Purpose**: Determines how features are grouped for analysis
  - across_categories: Analyzes all features together
  - within_categories: Analyzes features within their respective domains (e.g., cognitive, behavioral)

## Advanced Parameters

### Imputation Method (`imputer`)
- **Values**: "mean", "median", "kmeans", "mice"
- **Purpose**: Handles missing data
- **Impact**: Different methods may be more appropriate depending on the missingness pattern

### Data Preprocessing (`deal_with_na_values`)
- **Values**: "fill_with_zero", "drop", "impute_mean", "impute_median"
- **Purpose**: Preprocessing strategy for handling NA values
- **Trade-offs**: Balance between data preservation and quality

### Model Enhancement Options
- **ensemble_version**: Boolean for using ensemble learning
- **ensemble_type**: "bagging" or "stacking"
- **hyperparameter_tuning**: Boolean for optimization
- **with_optuna**: Boolean for using Optuna optimization
- **conformal_prediction**: Boolean for uncertainty quantification

### Feature Selection (`selection_method`)
- **Values**: 'rfecv', 'interaction', 'h-stats', 'clustering', 'None'
- **Purpose**: Method for selecting important features
- **Details**:
  - rfecv: Recursive Feature Elimination with Cross-Validation
  - interaction: Feature interaction analysis
  - h-stats: Hierarchy statistics
  - clustering: Feature clustering approach

### Isolation Analysis
- **isolate**: Boolean for category isolation
- **isolate_category**: Specific category to isolate
- **Purpose**: Detailed analysis of specific feature categories

### Quantile Analysis
- **quantile_segment**: Boolean for quantile-based analysis
- **Purpose**: Analysis of different segments of the outcome distribution

## Example Configurations

### Depression Onset Analysis
```python
tp_option = '2'
group = "None"
target_options = "dep_onset_rci_2.3"
split = "within_categories"
imputer = "kmeans"
ensemble_version = True
ensemble_type = "stacking"
```

### Gender-Specific Cognitive Analysis
```python
tp_option = '0'
group = "Female"
target_options = "tb_fluid"
split = "across_categories"
imputer = "mice"
selection_method = "interaction"
```

### Longitudinal Depression Trajectory
```python
tp_option = '4'
group = "high_ale"
target_options = "latent_class_depression"
split = "within_categories"
conformal_prediction = True
```

## Parameter Selection Guidelines

1. **Time Point Selection**:
   - Use T0 for baseline predictions
   - Use later timepoints for trajectory analysis
   - Consider T2 for stable outcomes

2. **Group Selection**:
   - Use "None" for population-level insights
   - Use specific groups for targeted analysis
   - Consider "high_ale" for vulnerability analysis

3. **Target Selection**:
   - Match to research question
   - Consider sample size implications
   - Check for outcome reliability

4. **Analysis Approach**:
   - Use "within_categories" for domain-specific insights
   - Use "across_categories" for comprehensive prediction
   - Consider computational resources

5. **Feature Selection**:
   - Use 'interaction' for complex relationships
   - Use 'rfecv' for dimension reduction
   - Use 'h-stats' for hierarchical relationships

## Notes
- Parameter combinations should align with research questions
- Consider computational resources for complex configurations
- Validate results across different parameter combinations
- Document parameter choices in publications
