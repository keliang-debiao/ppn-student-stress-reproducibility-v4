[README.md](https://github.com/user-attachments/files/28678970/README.md)
# PPN Student Stress Reproducibility Package

This repository contains the code and configuration used to reproduce the V4 manuscript results for:

**Multi-Factor Student Stress Prediction Based on a Psycho-Prototypical Network**

The package is designed for transparent peer-review reproduction. It includes leakage-safe preprocessing, deterministic split generation, random seeds, hyperparameter search spaces, baseline models, PPN training code, prototype decoding, calibration analysis, and figure/table generation.

## Data

The raw datasets are not redistributed in this repository. Download them from Kaggle and place the CSV files in `data/raw/`.

- Main dataset: Student Stress Factors: A Comprehensive Analysis  
  https://www.kaggle.com/datasets/rxnach/student-stress-factors-a-comprehensive-analysis
- Exploratory external dataset: Student Stress Monitoring Datasets  
  https://www.kaggle.com/datasets/mdsultanulislamovi/student-stress-monitoring-datasets

Expected main raw file name:

```text
data/raw/student_stress_factors.csv
```

Expected external raw file name:

```text
data/raw/student_stress_monitoring.csv
```

You can also try:

```bash
python scripts/download_data.py
```

Kaggle downloads require a local Kaggle/KaggleHub credential setup.

## Environment

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
pip install -e .
```

## One-command reproduction

```bash
python scripts/run_all.py --config configs/v4.yaml
```

This produces:

- `data/processed/split_indices_seed2021.csv`
- `results/run_v4/main_metrics.csv`
- `results/run_v4/repeated_seed_metrics.csv`
- `results/run_v4/confusion_matrix.csv`
- `results/run_v4/calibration_metrics.csv`
- `results/run_v4/ablation_metrics.csv`
- `results/run_v4/prototype_summaries.csv`
- `results/run_v4/prototype_feature_means_sd.csv`
- `results/run_v4/figures/figure5_performance.png` through `figure11_case.png`

## Manuscript constants

The manuscript used five random seeds:

```text
2021, 2022, 2023, 2024, 2025
```

The main split uses fixed class-specific held-out counts to match the V4 manuscript:

```text
low stress: 76
moderate stress: 73
high stress: 71
```

## Data and Code Availability Text

Before manuscript submission, replace the placeholder below with the final public or anonymous-review repository URL:

```text
[ANONYMIZED_REPOSITORY_URL_TO_BE_INSERTED_BEFORE_RESUBMISSION]
```

Suggested final sentence:

```text
The source code, exact preprocessing scripts, random seeds, hyperparameter configuration files, and train-test split indices are available in an anonymized repository: <URL>.
```

## Publishing to GitHub

This machine must have GitHub authentication before a remote repository can be created. If `GITHUB_TOKEN` is set to a personal access token with repository creation permission, run:

```powershell
$env:GITHUB_TOKEN = "<your-token>"
.\publish_to_github.ps1 -RepoName "ppn-student-stress-reproducibility-v4"
```

The script creates the GitHub repository through the GitHub API and pushes `main` without storing the token in the Git remote URL.
