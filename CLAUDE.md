# Personal Sleep Analysis

Shared conventions for all analysis projects are in `../CLAUDE.md` (loaded automatically).

## Dataset

- Source: personal sleep data (exported by hand, not from Kaggle); export source _TODO_
- Raw files: placed manually in `data/raw/` (not committed)
- Profile: `reports/data-profile.md`, regenerated with `.venv/bin/python scripts/profile_data.py`

## Data notes

<!-- Facts about the raw data that matter in every session: encoding, date formats,
     masked/empty/duplicate columns, missing values. Facts only, no findings. -->

- All three files are UTF-8 CSVs, joined on `night` (`%Y-%m-%d`). Range: 2025-09-19 to 2026-11-22.
- `night` is the evening the night starts: bedtimes from 00:00–04:59 belong to the previous date (98 nights).
- 12 calendar nights are absent from every file: 2025-10-03, 10-04, 10-17, 10-21, 11-07, 11-30; 2026-01-08, 03-13, 03-14, 08-09, 09-18, 09-21.
- **sleep_nightly.csv**: one row per night (418). `bedtime`/`wake_time` are `%Y-%m-%d %H:%M`.
  `asleep_min` = `core_min + deep_min + rem_min + unspecified_min` on every row. `in_bed_min` is 0 on every row.
  `unspecified_min` > 0 on 18 nights; core/deep/rem are all 0 on 2026-07-13, 2026-08-07 and 2026-09-16.
- **sleep_records.csv**: one row per raw Apple Health sample (17,075). `start`/`end` are `%Y-%m-%d %H:%M:%S`.
  `type` mixes three record kinds, and `value` changes meaning with it:
  `SleepAnalysis` = stage name (Core/Deep/REM/Awake/Unspecified, `unit` empty);
  `AppleSleepingWristTemperature` = number in degC; `AppleSleepingBreathingDisturbances` = number, unit `count`.
  So `value` is text and must be cast per type. `source` is constant (contains a curly apostrophe and a non-breaking space).
- **sleep_scores.csv**: one row per night (417). 2026-08-07 is missing here but present in sleep_nightly.
  `bedtime` is time of day only (`%H:%M`), with no date. `est_score` is 0–100 with `category` (Very Low/Low/OK/High/Excellent);
  Components: `duration_pts` (observed max 50), `bedtime_pts` (max 30), `interruption_pts` (max 20); their sum is
  within 1 point of `est_score` on all rows but one (off by 3.8).
  NaNs: `interruption_pts` 2, `wake_ups` 2, `bedtime_dev_min` 3. `notes` is filled on 5 rows only
  ("too little history: bedtime given full points", "no stage data: interruptions not scored").
