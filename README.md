# EEG_Mortality_Dataset_in_Parkinsons_Disease
# EEG Mortality Classification in Parkinson’s Disease (ds007020)

![EEG](https://upload.wikimedia.org/wikipedia/commons/6/6f/EEG_5min.png)

## Overview

This project demonstrates **EEG-based machine learning** for mortality classification in Parkinson’s Disease (PD) using the **OpenNeuro ds007020 dataset**.  
The dataset contains **resting-state EEG recordings** of individuals with PD, labeled as either *living* or *deceased*.  

The pipeline extracts **frequency band features** (delta, theta, alpha, beta, gamma) from EEG recordings and performs **Leave-One-Subject-Out (LOSO) cross-validation** using a linear SVM classifier.

> **Note:** This project is for **educational and methodological purposes**. Results should not be interpreted as clinical predictions.

---

## Dataset

**Source:** [OpenNeuro ds007020](https://openneuro.org/datasets/ds007020/versions/1.0.0)  
**Data Type:** Resting-state EEG (.vhdr, .eeg, .vmrk)  
**Sampling Rate:** 500 Hz  
**Montage:** Standard 10–20 EEG system  
**Labels:** `living` or `deceased`  
**Subjects:** Hundreds of anonymized participants following BIDS format  

---

## Project Structure

data1/
├── ds007020/
│ ├── sub-PD1001/
│ │ └── ses-01/
│ │ └── eeg/
│ │ ├── sub-PD1001_ses-01_task-rest_eeg.vhdr
│ │ ├── sub-PD1001_ses-01_task-rest_eeg.eeg
│ │ └── sub-PD1001_ses-01_task-rest_eeg.vmrk
│ └── participants.json
│ └── participants.tsv
│ └── dataset_description.json
notebooks/
├── eeg_ml_pipeline.ipynb
README.md


---

## Installation

```bash
# Clone this repository
git clone https://github.com/abm984/EEG_Mortality_Dataset_in_Parkinsons_Disease.git
cd eeg-mortality-pd

# Install dependencies
pip install mne mne-bids openneuro-py scikit-learn pandas numpy

# Step 1: Download dataset
from openneuro import download
download(dataset="ds007020", target_dir="data1", include=None)

# Step 2: Run EEG feature extraction and classification
# See notebooks/eeg_ml_pipeline.ipynb for full code


Features Extracted

Band power in delta (1-4 Hz)

Band power in theta (4-8 Hz)

Band power in alpha (8-13 Hz)

Band power in beta (13-30 Hz)

Band power in gamma (30-40 Hz)

Extracted per channel across all EEG electrodes

ML Pipeline

Preprocessing: Bandpass filter (1-40 Hz), average reference

Feature extraction: Power spectral density (Welch method)

Classifier: Linear Support Vector Machine (SVM)

Validation: Leave-One-Subject-Out (LOSO) cross-validation



Future Improvements

Include all subjects for robust evaluation

Use per-channel relative band power

Apply dimensionality reduction (PCA, LDA)

Explore advanced classifiers (Random Forest, XGBoost, EEGNet)

Visualize EEG spectra and topographic maps

References

OpenNeuro ds007020

Gramfort, A. et al., MNE-Python: software for processing EEG and MEG data, NeuroImage, 2013












