# Data Directory

This directory is designated for storing datasets used in the Credit Risk Analysis project.

## Overview

The data folder contains the datasets required for training, testing, and validating credit risk models. Due to privacy and size considerations, raw data files are not included in this repository.

## Data Requirements

### Expected Data Files

The following data files should be placed in this directory:

1. **credit_data.csv** - Main credit risk dataset
   - Contains customer information and credit history
   - Features: credit score, income, loan amount, employment history, etc.
   - Target variable: default status (binary: 0/1)

2. **train_data.csv** - Training dataset
   - Preprocessed training data
   - Used for model training

3. **test_data.csv** - Testing dataset
   - Preprocessed testing data
   - Used for model evaluation

## Getting Data

### Option 1: Public Datasets

You can use publicly available credit risk datasets:

- [Kaggle Credit Risk Datasets](https://www.kaggle.com/datasets?search=credit+risk)
- [UCI Machine Learning Repository - Credit Datasets](https://archive.ics.uci.edu/ml/datasets.php)
- [LendingClub Data](https://www.lendingclub.com/statistics/additional-statistics)

### Option 2: Synthetic Data

For testing purposes, you can generate synthetic credit data using Python:

```python
import pandas as pd
import numpy as np
from sklearn.datasets import make_classification

# Generate synthetic credit risk data
X, y = make_classification(
    n_samples=10000,
    n_features=20,
    n_informative=15,
    n_redundant=5,
    random_state=42
)

# Create DataFrame
feature_names = [f'feature_{i}' for i in range(20)]
df = pd.DataFrame(X, columns=feature_names)
df['default'] = y

# Save to CSV
df.to_csv('credit_data.csv', index=False)
```

## Data Privacy

**Important**: Never commit sensitive or personally identifiable information (PII) to this repository.

- Ensure all data is properly anonymized
- Remove or mask sensitive fields (names, addresses, social security numbers, etc.)
- Use synthetic data for examples and demonstrations
- Add actual data files to `.gitignore`

## Data Format Guidelines

### CSV Format

- Use comma-separated values (CSV) format
- Include headers in the first row
- Use UTF-8 encoding
- Missing values should be represented consistently (e.g., empty string or 'NaN')

### Example Data Structure

```csv
credit_score,income,loan_amount,employment_years,debt_ratio,default
720,50000,15000,5,0.35,0
650,35000,20000,2,0.45,1
800,80000,25000,10,0.25,0
```

## Data Preprocessing

Before using the data:

1. Check for missing values
2. Handle outliers
3. Encode categorical variables
4. Scale numerical features
5. Split into training and testing sets

## Sample Data

A small sample dataset is available for initial testing:

- `sample_credit_data.csv` - Contains 100 anonymized sample records
- Use this to verify your code works before processing full datasets

## Notes

- Large data files (>100MB) should be stored externally
- Consider using data versioning tools like DVC for large datasets
- Document any data transformations in your notebooks
- Keep track of data sources and licenses
