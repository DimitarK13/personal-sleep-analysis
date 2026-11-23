# Data Profile

_Generated 2026-11-23 14:25 by `scripts/profile_data.py`. Re-run the script to regenerate this file, and don't edit it by hand._

This file lists facts about the raw data and flags things to check. It doesn't interpret them; the decisions belong in the data-preparation notebook.

| File                                  | Rows   | Columns | Size   | Encoding | Flags |
| ------------------------------------- | ------ | ------- | ------ | -------- | ----- |
| [sleep_nightly.csv](#sleepnightlycsv) | 418    | 10      | 0.0 MB | `utf-8`  | 11    |
| [sleep_records.csv](#sleeprecordscsv) | 17,075 | 8       | 1.8 MB | `utf-8`  | 6     |
| [sleep_scores.csv](#sleepscorescsv)   | 417    | 12      | 0.0 MB | `utf-8`  | 13    |

## sleep_nightly.csv

- **Rows × columns:** 418 × 10
- **Read with:** `utf-8`
- **Memory in pandas:** 0 MB
- **Fully duplicated rows:** none
- **Columns with missing values:** 0 of 10

### Flags

_Things to check before cleaning. Each one may be fine; that's for you to decide._

**1:1 mappings** (each value of one column matches exactly one value of the other, e.g. an ID and its name):

- `night` ↔ `bedtime`
- `night` ↔ `wake_time`
- `bedtime` ↔ `wake_time`

**Constant columns:**

- `in_bed_min`: single value '0' in every non-missing row

**Dates stored as text:**

- `night`: dates stored as text (format `%Y-%m-%d`)
- `bedtime`: dates stored as text (format `%Y-%m-%d %H:%M`)
- `wake_time`: dates stored as text (format `%Y-%m-%d %H:%M`)

**Many IQR outliers (≥5%):**

- `awake_min`: 7.7% of values outside 1.5×IQR

**Row identifiers:**

- `night`: unique in every row (row identifier?)
- `bedtime`: unique in every row (row identifier?)
- `wake_time`: unique in every row (row identifier?)

### Columns

| #   | Column            | Type              | Missing | Unique | Most common values                                   |
| --- | ----------------- | ----------------- | ------- | ------ | ---------------------------------------------------- |
| 1   | `night`           | date (text) (str) | –       | 418    | 2025-09-19, 2025-09-20, 2025-09-21                   |
| 2   | `bedtime`         | date (text) (str) | –       | 418    | 2025-09-19 23:38, 2025-09-20 21:56, 2025-09-21 22:00 |
| 3   | `wake_time`       | date (text) (str) | –       | 418    | 2025-09-20 06:49, 2025-09-21 07:38, 2025-09-22 06:30 |
| 4   | `asleep_min`      | numeric (float64) | –       | 306    | 458.5, 521.2, 441.1                                  |
| 5   | `core_min`        | numeric (float64) | –       | 292    | 307.2, 324.6, 285.3                                  |
| 6   | `deep_min`        | numeric (float64) | –       | 166    | 42.3, 65.2, 50.8                                     |
| 7   | `rem_min`         | numeric (float64) | –       | 210    | 116, 115, 123.5                                      |
| 8   | `awake_min`       | numeric (float64) | –       | 156    | 16.9, 18.9, 12.9                                     |
| 9   | `unspecified_min` | numeric (float64) | –       | 18     | 0, 80.1, 270.9                                       |
| 10  | `in_bed_min`      | numeric (int64)   | –       | 1      | 0                                                    |

### Numeric columns

| Column            | Min   | 25%    | Median | Mean   | 75%    | Max    | Std   | Zeros  | Negative | IQR outliers |
| ----------------- | ----- | ------ | ------ | ------ | ------ | ------ | ----- | ------ | -------- | ------------ |
| `asleep_min`      | 89.10 | 438.48 | 475.50 | 467.64 | 507.18 | 665.10 | 65.44 | 0%     | 0%       | 4.5%         |
| `core_min`        | 0     | 273.30 | 300.70 | 298.22 | 331    | 462    | 54.01 | 0.7%   | 0%       | 3.3%         |
| `deep_min`        | 0     | 40.50  | 53.30  | 53.75  | 64.70  | 106.50 | 16.90 | 0.7%   | 0%       | 1.2%         |
| `rem_min`         | 0     | 97.60  | 113.50 | 110.78 | 126.97 | 178.20 | 26.97 | 0.7%   | 0%       | 3.1%         |
| `awake_min`       | 3     | 14.40  | 21.35  | 27.47  | 28.40  | 412.10 | 31.79 | 0%     | 0%       | 7.7%         |
| `unspecified_min` | 0     | 0      | 0      | 4.90   | 0      | 270.90 | 25.93 | 95.7%  | 0%       | 0%           |
| `in_bed_min`      | 0     | 0      | 0      | 0      | 0      | 0      | 0     | 100.0% | 0%       | 0%           |

### Date/time columns

| Column      | Format           | Earliest         | Latest           | Span (days) | Distinct days | Unparsed |
| ----------- | ---------------- | ---------------- | ---------------- | ----------- | ------------- | -------- |
| `night`     | `%Y-%m-%d`       | 2025-09-19       | 2026-11-22       | 429         | 418           | 0        |
| `bedtime`   | `%Y-%m-%d %H:%M` | 2025-09-19 23:38 | 2026-11-23 01:28 | 429         | 359           | 0        |
| `wake_time` | `%Y-%m-%d %H:%M` | 2025-09-20 06:49 | 2026-11-23 10:35 | 429         | 418           | 0        |

### Value distributions (columns with ≤25 distinct values)

- **`unspecified_min`** (18): 0 95.7% · 80.1 0.5% · 270.9 0.2% · 65.2 0.2% · 82.7 0.2% · 159.3 0.2% · … +12 more

## sleep_records.csv

- **Rows × columns:** 17,075 × 8
- **Read with:** `utf-8`
- **Memory in pandas:** 8 MB
- **Fully duplicated rows:** none
- **Columns with missing values:** 1 of 8

### Flags

_Things to check before cleaning. Each one may be fine; that's for you to decide._

**Constant columns:**

- `source`: single value 'Dimitar’s Apple\xa0Watch' in every non-missing row

**Mostly missing (≥50%):**

- `unit`: 95.2% missing

**Dates stored as text:**

- `night`: dates stored as text (format `%Y-%m-%d`)
- `start`: dates stored as text (format `%Y-%m-%d %H:%M:%S`)
- `end`: dates stored as text (format `%Y-%m-%d %H:%M:%S`)

**Many IQR outliers (≥5%):**

- `duration_min`: 7.9% of values outside 1.5×IQR

### Columns

| #   | Column         | Type              | Missing        | Unique | Most common values                                                |
| --- | -------------- | ----------------- | -------------- | ------ | ----------------------------------------------------------------- |
| 1   | `night`        | date (text) (str) | –              | 418    | 2025-09-28, 2025-12-23, 2025-09-29                                |
| 2   | `type`         | text (str)        | –              | 3      | SleepAnalysis, AppleSleepingWristTempe…, AppleSleepingBreathingD… |
| 3   | `value`        | text (str)        | –              | 811    | Core, Awake, REM                                                  |
| 4   | `unit`         | text (str)        | 16,249 (95.2%) | 2      | degC, count                                                       |
| 5   | `start`        | date (text) (str) | –              | 17,059 | 2025-09-26 21:37:57, 2025-09-30 22:35:58, 2025-11-09 02:37:09     |
| 6   | `end`          | date (text) (str) | –              | 17,072 | 2025-09-28 08:20:09, 2026-03-10 06:59:09, 2026-09-05 07:00:01     |
| 7   | `duration_min` | numeric (float64) | –              | 922    | 1, 0.5, 1.5                                                       |
| 8   | `source`       | text (str)        | –              | 1      | Dimitar’s Apple Watch                                             |

### Numeric columns

| Column         | Min  | 25% | Median | Mean  | 75%   | Max    | Std    | Zeros | Negative | IQR outliers |
| -------------- | ---- | --- | ------ | ----- | ----- | ------ | ------ | ----- | -------- | ------------ |
| `duration_min` | 0.48 | 2   | 7.95   | 35.68 | 21.40 | 812.03 | 103.57 | 0%    | 0%       | 7.9%         |

### Date/time columns

| Column  | Format              | Earliest         | Latest           | Span (days) | Distinct days | Unparsed |
| ------- | ------------------- | ---------------- | ---------------- | ----------- | ------------- | -------- |
| `night` | `%Y-%m-%d`          | 2025-09-19       | 2026-11-22       | 429         | 418           | 0        |
| `start` | `%Y-%m-%d %H:%M:%S` | 2025-09-19 23:29 | 2026-11-23 10:26 | 429         | 428           | 0        |
| `end`   | `%Y-%m-%d %H:%M:%S` | 2025-09-19 23:56 | 2026-11-23 11:12 | 429         | 426           | 0        |

### Value distributions (columns with ≤25 distinct values)

- **`type`** (3): SleepAnalysis 95.2% · AppleSleepingWristTemperature 2.4% · AppleSleepingBreathingDisturb… 2.4%
- **`unit`** (2): degC 2.4% · count 2.4% · _missing_ 95.2%

## sleep_scores.csv

- **Rows × columns:** 417 × 12
- **Read with:** `utf-8`
- **Memory in pandas:** 0 MB
- **Fully duplicated rows:** none
- **Columns with missing values:** 4 of 12

### Flags

_Things to check before cleaning. Each one may be fine; that's for you to decide._

**Mostly missing (≥50%):**

- `notes`: 98.8% missing

**Dates stored as text:**

- `night`: dates stored as text (format `%Y-%m-%d`)
- `bedtime`: dates stored as text (format `mixed formats`)

**Whole numbers stored as float:**

- `bedtime_dev_min`: whole numbers stored as float (because of missing values)
- `wake_ups`: whole numbers stored as float (because of missing values)

**Many IQR outliers (≥5%):**

- `est_score`: 10.1% of values outside 1.5×IQR
- `duration_pts`: 18.7% of values outside 1.5×IQR
- `bedtime_pts`: 7.7% of values outside 1.5×IQR
- `interruption_pts`: 12.3% of values outside 1.5×IQR
- `asleep_h`: 5.0% of values outside 1.5×IQR
- `bedtime_dev_min`: 5.3% of values outside 1.5×IQR
- `awake_min`: 7.7% of values outside 1.5×IQR

**Row identifiers:**

- `night`: unique in every row (row identifier?)

### Columns

| #   | Column             | Type              | Missing     | Unique | Most common values                                 |
| --- | ------------------ | ----------------- | ----------- | ------ | -------------------------------------------------- |
| 1   | `night`            | date (text) (str) | –           | 417    | 2025-09-19, 2025-09-20, 2025-09-21                 |
| 2   | `est_score`        | numeric (int64)   | –           | 61     | 89, 90, 88                                         |
| 3   | `category`         | text (str)        | –           | 5      | High, OK, Low                                      |
| 4   | `duration_pts`     | numeric (float64) | –           | 99     | 50, 45.6, 47.9                                     |
| 5   | `bedtime_pts`      | numeric (float64) | –           | 122    | 30, 0, 28.1                                        |
| 6   | `interruption_pts` | numeric (float64) | 2 (0.5%)    | 110    | 0, 15.2, 8.7                                       |
| 7   | `asleep_h`         | numeric (float64) | –           | 233    | 7.19, 7.96, 7.97                                   |
| 8   | `bedtime`          | date (text) (str) | –           | 212    | 22:53, 23:18, 22:59                                |
| 9   | `bedtime_dev_min`  | numeric (float64) | 3 (0.7%)    | 122    | 2, 6, 16                                           |
| 10  | `wake_ups`         | numeric (float64) | 2 (0.5%)    | 20     | 8, 7, 9                                            |
| 11  | `awake_min`        | numeric (float64) | –           | 156    | 16.9, 18.9, 12.9                                   |
| 12  | `notes`            | text (str)        | 412 (98.8%) | 2      | too little history: bed…, no stage data: interrup… |

### Numeric columns

| Column             | Min  | 25%   | Median | Mean  | 75%   | Max    | Std   | Zeros | Negative | IQR outliers |
| ------------------ | ---- | ----- | ------ | ----- | ----- | ------ | ----- | ----- | -------- | ------------ |
| `est_score`        | 0    | 79    | 86     | 81.20 | 89    | 100    | 13.95 | 0.2%  | 0%       | 10.1%        |
| `duration_pts`     | 0    | 47.90 | 50     | 46.38 | 50    | 50     | 8.53  | 0.7%  | 0%       | 18.7%        |
| `bedtime_pts`      | 0    | 23.60 | 29.70  | 25.51 | 30    | 30     | 7.42  | 3.8%  | 0%       | 7.7%         |
| `interruption_pts` | 0    | 7.70  | 9.40   | 9.32  | 11.30 | 20     | 4.03  | 5.8%  | 0%       | 12.3%        |
| `asleep_h`         | 2.54 | 7.35  | 7.92   | 7.81  | 8.46  | 11.09  | 1.05  | 0%    | 0%       | 5.0%         |
| `bedtime_dev_min`  | 0    | 12    | 32     | 50.97 | 62    | 594    | 75.13 | 1.7%  | 0%       | 5.3%         |
| `wake_ups`         | 1    | 6     | 8      | 8.11  | 10    | 21     | 3.37  | 0%    | 0%       | 2.4%         |
| `awake_min`        | 3    | 14.40 | 21.40  | 27.53 | 28.40 | 412.10 | 31.81 | 0%    | 0%       | 7.7%         |

### Date/time columns

| Column    | Format          | Earliest         | Latest           | Span (days) | Distinct days | Unparsed |
| --------- | --------------- | ---------------- | ---------------- | ----------- | ------------- | -------- |
| `night`   | `%Y-%m-%d`      | 2025-09-19       | 2026-11-22       | 429         | 417           | 0        |
| `bedtime` | `mixed formats` | 2026-11-23 00:01 | 2026-11-23 23:59 | 0           | 1             | 0        |

### Value distributions (columns with ≤25 distinct values)

- **`category`** (5): High 66.7% · OK 21.8% · Low 6.2% · Very Low 2.6% · Excellent 2.6%
- **`wake_ups`** (20): 8 13.7% · 7 13.2% · 9 11.5% · 6 11.3% · 10 9.6% · 5 7.9% · … +14 more · _missing_ 0.5%
- **`notes`** (2): too little history: bedtime g… 0.7% · no stage data: interruptions … 0.5% · _missing_ 98.8%
