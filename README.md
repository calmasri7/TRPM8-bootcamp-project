# Project Overview

The goal of this project is to predict the potency of molecules on the TRPM8 drug target using their physical, chemical, and topological properties. The project addresses two main predictive tasks: potency classification (e.g., high, medium or low potency) and IC50 value prediction (regression). The workflow is divided into five stages: preprocessing the dataset to clean and standardize activity data (`1_preprocess`), generating a comprehensive set of molecular descriptors (`2_descriptors`), splitting the data into training and testing sets for regression and classification tasks (`3_train_test_split`), performing feature selection using five distinct methods to identify the most relevant descriptors (`4_feature_selection`), and training four machine learning models on the reduced feature sets (`5_model_training`). The optimal combination of feature selection method and machine learning model is chosen based on predictive performance metrics.

---

## Directory Structure

This repository contains the following main directories:

```
TRPM8-bootcamp-project/
├─1_preprocess/
│   ├─ preprocess.ipynb
│   ├─ TRPM8-homosapien-compounds-activities.csv
│   └─ TRPM8-homosapien-compounds-activities-processed.csv
├─2_descriptors/
│   ├─ 3D-descriptors.ipynb
│   ├─ physicochemical-descriptors.ipynb
│   ├─ quantum-descriptors.ipynb
│   ├─ topological-descriptors.ipynb
│   └─ *-descriptors.csv *-descriptors-standardized.csv
└─3_train_test_split/
    ├─ train_test_stratify.ipynb
    ├─ descriptors_all.csv
    └─ train*.csv test*.csv val*.csv
```

---

## Directory Details

### 1_preprocess

This directory contains scripts and data for the initial preprocessing of activity data.

- **`preprocess.ipynb`**: A Jupyter Notebook that processes activity data for Homo sapiens TRPM8 obtained from [Chembl Activity Data](https://www.ebi.ac.uk/chembl/web_components/explore/target/CHEMBL1075319). The preprocessing steps include:
  - Removing empty activity values, salt ions, and small fragments.
  - Ensuring correct SMILES representation.
  - Removing duplicates.
  - Standardizing IC50 data.

- **`TRPM8-homosapien-compounds-activities.csv`**: Input activity data file downloaded from Chembl.

- **`TRPM8-homosapien-compounds-activities-processed.csv`**: Output data file after preprocessing with `preprocess.ipynb`.

---

### 2_descriptors

This directory contains scripts for generating various molecular descriptors.

- **`3D-descriptors.ipynb`**: Extracts 3D molecular descriptors.
- **`physicochemical-descriptors.ipynb`**: Extracts physicochemical descriptors.
- **`quantum-descriptors.ipynb`**: Extracts quantum descriptors.
- **`topological-descriptors.ipynb`**: Extracts 2D topological descriptors.
- **Outputs**:
  - `[descriptor_name]-descriptors.csv`: Raw descriptor data.
  - `[descriptor_name]-descriptors-standardized.csv`: Standardized descriptor data.

---

### 3_train_test_split

This directory contains files and scripts for splitting the data into training and testing datasets.

- **`descriptors_all.csv`**: Combined descriptor data from `2_descriptors`, including columns for potency values (classification) and IC50 values (regression).
- **`train_test_stratify.ipynb`**: A script that splits the data as follows:
  - **Training Set**: 85% of the data.
  - **Test Set**: 15% of the data.
  - **Train/Validation Split**: Further splits the training set into 5-fold cross-validation.
- **Outputs**:
  - `train_reg.csv`, `train_class.csv`: Training sets for regression and classification tasks.
  - `test_reg.csv`, `test_class.csv`: Test sets for regression and classification tasks.
  - `train_[reg_or_class]_k.csv` and `val_[reg_or_class]_k.csv`: Training and validation sets for each fold (k) in cross-validation for regression and classification tasks.

---

