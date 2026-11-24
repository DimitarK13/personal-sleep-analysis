# Personal Sleep Analysis

## 1. Project Overview

This project aims to investigate sleeping patterns using my personal sleep data, recorded with an Apple Watch, over the span of 418 days. The analysis is ultimately to improve day-to-day sleep.

## 2. Problem Statement

This analysis is a personal project, to help me understand better my sleeping habits. If I can understand better when I tend to wake up more, I can ultimately take some actions in order to prevent them.

## 3. Objectives

- Discover during which seasons I tend to wake up more.
- Discover during which parts of the night I tend to wake up more.
- Measure how bedtime, and how consistent it is from night to night, relates to my sleep score and to the amount of deep and REM sleep.
- Identify which part of the sleep score (duration, bedtime or interruptions) most often pulls it down.

## 4. Research Questions

- Is there a relation between seasons and good sleep?
- Does going to bed early result in a better sleep?
- Are there patterns in wake ups during the night?

## 5. Hypotheses

- Worse overall sleeping scores during the summer.
- Going to bed later results to better sleep.

## 6. Data Quality Assessment

- Dropped columns: bedtime_y, awake_min_y and notes, as they were either duplicate columns or too many missing values.
- Renamed columns: bedtime_x to bedtime, awake_min_x to awake_min.
- Dropped rows where interruption_pts and wake_ups are missing (2 rows).
- Converted night, bedtime (former bedtime_x) and wake_time to datetime formats.
- Converted wake_ups to integer (it was stored as float because of missing values).
- For the bedtime analysis, left out 6 nights with a bedtime in the afternoon (13:12–15:34). These nights have 7–11 hours asleep, so the recorded bedtime is most likely the start of an afternoon nap that got merged into the night.

## 7. Analysis

### Is there a relation between seasons and good sleep?

In order to answer this question, I looked at three things:

1. Average sleep score by month
2. Average wake ups by month
3. Bedtime (before or after midnight) by month

#### Average Sleep Score by Month

The average sleep score by month showed that both the lowest average and highest average sleep score are both in summer - June 2026 and July 2026. However, winter is more often below the overall average sleep score, compared to summer.

Summer and autumn seem to have the overall highest average scores, and there seems to be slight positive general trend, but it's hard to bring any conclusions with just one year of data.

![Average Sleep Score by Month](../visualizations/average-sleep-score-by-month.png)

#### Average Wake Ups by Month

The average amount of wake ups per month seems to be telling a similar story as the average sleep score, but with more variability. July and August 2026 are the months with least amount of wake ups, but also November 2025 and January 2026 have similar average amounts.

With the amount of wake ups there doesn't seem to be any general trend.

![Average Wake Ups by Month](../visualizations/average-wake-ups-by-month.png)

#### Bedtime (Before or After Midnight) by Month

It seems that months where I go to bed after 00:00, I seem to be getting higher sleeping scores overall, with fewer wake ups.

![Bedtime (Before or After Midnight) by Month](../visualizations/bedtime-before-vs-after-midnight.png)

### Does going to bed early result in a better sleep?

To answer this question, I compared bedtime (as a clock time) with the sleep score and its three components, time asleep, wake ups (in total and per hour asleep) and deep and REM sleep, over 409 nights. I split the nights into four bedtime groups: before 22:30 (95 nights), 22:30–23:30 (158), 23:30–00:30 (98) and after 00:30 (58).

#### Sleep Score by Bedtime

The best scores come with a bedtime between 22:30 and 23:30 (mean 85.9, median 88). Going to bed earlier than that doesn't help: before 22:30 the mean score is 82.6. After 00:30 the score drops sharply to a mean of 67.8, with a much wider spread. Some late nights still score in the 90s, but most of the very low scores are in this group.

![Sleep Score by Bedtime](../visualizations/sleep-score-by-bedtime.png)

#### Points Lost by Bedtime

After 00:30 the extra lost points come from duration (9.3 points lost vs 1.4–3.8 in the other groups) and bedtime consistency (13.0 vs 1.5–3.6). The consistency score rewards a regular bedtime, and bedtimes that late are unusual for me. Before 22:30, interruptions cost the most points (12.4), because these nights have the most wake ups per hour asleep (1.18 vs about 1.0 in the other groups). 22:30–23:30 loses the fewest points overall (14.1).

![Points Lost by Bedtime](../visualizations/points-lost-by-bedtime.png)

#### Time Asleep by Bedtime

Time asleep has the strongest relation with bedtime (Spearman r = −0.34). It goes from about 8.7 hours for a bedtime around 20:30 down to about 6.3 hours around 04:00, so on average getting up later after a late night doesn't make up for the lost sleep.

Later bedtimes come with fewer wake ups in total (r = −0.24), but mostly because a shorter night has less time to wake up in; per hour asleep the relation is weak (r = −0.13). The share of deep (11–12%) and REM (23–24%) sleep is about the same for every bedtime. Later bedtimes only mean fewer minutes of each because the night is shorter.

![Time Asleep by Bedtime](../visualizations/time-asleep-by-bedtime.png)

## 8. Conclusions and Recommendations

### Does going to bed early result in a better sleep?

Going to bed early does not by itself give a better sleep, but going to bed late does give a worse one.

- My best nights start between 22:30 and 23:30. Going to bed earlier than that gives longer nights, but with more wake ups per hour.
- A bedtime after 00:30 lowers the score sharply (mean 67.8 vs 82.6–85.9 in the other groups), mostly because I sleep less and because those bedtimes are irregular for me.
- Bedtime doesn't change how much of the night is deep or REM sleep.

The hypothesis that going to bed later results in better sleep is not supported. The month-level comparison (months with more late bedtimes seeming to score higher) doesn't hold when looking at individual nights. These are correlations, not causes: late nights can have their own reasons (going out, stress, vacation) that also affect how I sleep.

**Recommendation:** aim for a bedtime between 22:30 and 23:30, and avoid going to bed after 00:30.

## 9. Limitations

- The data can't uncover causations for bad sleeping scores.
