# EEG Signal Processing Pipeline for Visual Prediction-Error Analysis

This repository is a public technical case-study version of an EEG analysis pipeline developed for a visual prediction-error experiment.

The original EEG dataset is confidential and is not included. This repository therefore does **not** reproduce the full analysis end-to-end from raw recordings. Instead, it documents the processing workflow and provides selected, sanitized code excerpts and representative figure placeholders for each stage of the pipeline.

## Public Repository Scope

Included:

- Stage-by-stage pipeline documentation
- Selected code excerpts that demonstrate the main processing logic
- Figure folders for representative outputs from each stage
- Data availability and privacy notes
- A machine-learning extension plan currently in development

Not included:

- Raw EEG recordings
- Participant-level data files
- Lab-internal paths
- Full intermediate outputs
- Complete private analysis directories
- Final machine-learning results

## Project Overview

The pipeline was developed to analyze neural responses to prediction violations in structured visual sequences. The analysis focuses on EEG preprocessing, artifact rejection, spectral analysis, time-frequency analysis, phase consistency, dB contrasts between experimental conditions, and non-parametric cluster-based statistics.

## Main Methods

- EEG preprocessing with Python and MNE
- Channel setup, montage assignment, and average referencing
- Notch filtering and high-pass filtering
- Bad-channel detection and interpolation
- ICA-based artifact handling
- Epoch creation and automated noisy-epoch rejection
- Welch PSD estimation
- dB contrasts between experimental conditions
- Complex Morlet time-frequency analysis
- Inter-trial coherence analysis
- Cluster-based permutation testing
- ROI-based and topographic visualization
- ML feature extraction extension in development

## Repository Structure

```text
eeg-signal-processing-case-study/
├── README.md
├── requirements.txt
├── .gitignore
├── config/
│   └── example_config.py
├── docs/
│   ├── data_availability.md
│   ├── methods_summary.md
│   └── pipeline_overview.md
├── stages/
│   ├── 01_preprocessing_channel_cleaning/
│   ├── 02_epoch_cleaning/
│   ├── 03_psd_analysis/
│   ├── 04_psd_db_contrasts/
│   ├── 05_psd_cluster_statistics/
│   ├── 06_complex_morlet_tfr/
│   ├── 07_tfr_power_computation/
│   ├── 08_itc_phase_analysis/
│   ├── 09_tfr_cluster_statistics/
│   ├── 10_roi_tf_cluster_statistics/
│   └── 11_band_avg_spatiotemporal_topomaps/
└── ml_extension/
    ├── README.md
    ├── feature_extraction_plan.md
    └── code_skeleton.py
```

## Pipeline Stages

| Stage | Folder | Purpose |
|---|---|---|
| 01 | `01_preprocessing_channel_cleaning` | Clean continuous EEG, detect bad channels, interpolate, apply ICA |
| 02 | `02_epoch_cleaning` | Segment data into epochs and reject noisy epochs |
| 03 | `03_psd_analysis` | Compute Welch PSD per epoch, subject, and group |
| 04 | `04_psd_db_contrasts` | Compute log-ratio PSD contrasts between conditions |
| 05 | `05_psd_cluster_statistics` | Test PSD contrasts with frequency × channel cluster permutation |
| 06 | `06_complex_morlet_tfr` | Compute complex Morlet TFR per epoch |
| 07 | `07_tfr_power_computation` | Convert complex TFR to power and preserve full dimensions |
| 08 | `08_itc_phase_analysis` | Compute phase consistency / inter-trial coherence |
| 09 | `09_tfr_cluster_statistics` | Run time × frequency × channel cluster statistics |
| 10 | `10_roi_tf_cluster_statistics` | Average by ROI and test frequency × time clusters |
| 11 | `11_band_avg_spatiotemporal_topomaps` | Average by frequency band and create topographic cluster summaries |

## Machine-Learning Extension

A machine-learning extension is currently in development. The goal is to transform cleaned EEG epochs and spectral/time-frequency outputs into trial-level feature matrices for classification.

Planned focus:

- Spectral feature extraction from selected channels, frequency bands, and time windows
- Trial-level feature matrices
- Baseline linear classifiers such as LDA and logistic regression
- Cross-validated evaluation
- Chance-level comparison

Final ML results are not included yet.

## Installation

```bash
python -m venv .venv
```

Windows:

```bash
.venv\Scripts\activate
```

macOS / Linux:

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## Data Availability

The original EEG data are confidential and are not included in this repository. See `docs/data_availability.md` for details.

## Keywords

EEG, neural signal processing, Python, MNE, preprocessing, artifact rejection, PSD, Morlet wavelets, time-frequency analysis, ITC, permutation statistics, cluster-based correction, cognitive neuroscience, machine-learning feature extraction.
