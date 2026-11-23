# Personal Sleep Analysis

## Overview

Analyzing personal sleep patterns and scores

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python scripts/profile_data.py    # writes a data-quality profile to reports/data-profile.md
```

## Dataset

- Source: personal sleep data, _TODO_ (device/app and how it was exported). Put the exported files in `data/raw/`.
- Coverage: _TODO_
- Time period: _TODO_

## Research Questions

- _TODO_

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## Project Structure

```text
personal-sleep-analysis/
├── data/
│   ├── raw/        # Original exported data (not committed)
│   └── processed/  # Cleaned data from 02-data-preparation (not committed)
├── notebooks/      # 01 initial analysis, 02 data preparation, 03 exploratory analysis
├── reports/        # report.md (analytical report), data-profile.md (generated)
├── visualizations/ # Exported charts used in the report
├── scripts/        # profile_data.py
├── README.md
├── requirements.txt
└── .gitignore
```
