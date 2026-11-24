# Personal Sleep Analysis

## Overview

Analyzing personal sleep patterns and scores.

## Setup

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python scripts/profile_data.py    # writes a data-quality profile to reports/data-profile.md
```

## Dataset

- Source: personal sleep data, tracked with Apple Watch Series 11, exported through Apple Health app.
- Coverage: bedtime, wake up time, time asleep, time spent in each mode.
- Time period: 19 September 2025 - 22 November 2026

## Research Questions

- Is there a relation between seasons and good sleep?
- Does going to bed early result in a better sleep?
- Are there patterns in wake ups during the night?

## Key Findings

- **Seasons:** no strong relation. Monthly average scores stay between 77 and 86, and the hypothesis of worse sleep in summer is not supported (June was the worst month, but July and August among the best).
- **Bedtime:** going to bed early doesn't give a better sleep, but going to bed late gives a worse one. The best nights start between 22:30 and 23:30; after 00:30 the average score drops from about 83–86 to 68, mostly because of shorter and less regular sleep.
- **Wake ups:** I wake up most early in the night, with a peak roughly 50 to 100 minutes after going to bed. 93% of wake ups last less than 5 minutes. The day of the week makes little difference.
- **Sleep score:** interruptions are the biggest point loss on 79% of the nights, more than duration or bedtime consistency.

The full analysis, charts and limitations are in the [report](reports/report.md).

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
