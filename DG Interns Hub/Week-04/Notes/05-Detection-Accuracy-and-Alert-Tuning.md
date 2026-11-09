# 5. Detection Accuracy: True Positives, False Positives and Tuning

## Core detection outcomes
A detection outcome is determined by comparing what the rule reported with what actually happened.

| Outcome | Meaning | Example |
|---|---|---|
| True Positive (TP) | Detection alerts on genuinely suspicious or malicious activity | A confirmed password-guessing test triggers a brute-force rule |
| False Positive (FP) | Detection alerts on benign activity | An approved monitoring system triggers a scan alert |
| True Negative (TN) | Detection correctly does not alert on benign activity | Normal sign-ins do not trigger a brute-force rule |
| False Negative (FN) | Malicious activity occurs but the detection fails to alert | A slow password attack stays below the configured threshold |

These labels require investigation or reliable ground truth. An alert alone cannot establish whether it is a TP or FP.

## Alert fatigue
Alert fatigue occurs when analysts receive so many alerts, especially repetitive or low-value alerts, that important activity becomes harder to identify and prioritize.

Common causes:
- Overly broad detection conditions.
- Repeated alerts for the same underlying activity.
- Poorly parsed or duplicated data.
- Thresholds that do not reflect normal behavior.
- Missing context such as asset criticality or user role.

Consequences can include delayed investigations, missed high-risk events and analyst burnout.

## Detection tuning

| Tuning action | How it helps | Example |
|---|---|---|
| Validate data quality | Prevents incorrect matches caused by missing or incorrect fields | Confirm src_ip is the true source address |
| Adjust thresholds | Aligns rule with observed behavior | Five failures in five minutes rather than five in a day |
| Add context | Improves prioritization | Raise priority when a privileged account is targeted |
| Deduplicate | Reduces repeated notifications | Group repeated events into one alert window |
| Use allowlists carefully | Suppresses verified benign activity in a narrow context | Exclude a documented scanner from a specific scan rule |
| Test both cases | Measures false positives and false negatives | Test normal and controlled failed logons |
| Review regularly | Keeps detections useful as systems change | Reassess after a new application is deployed |

## Example: repeated failed logons
Suppose a rule alerts when an account has five failed sign-ins in five minutes.

- If a controlled test produces five failures and the rule alerts, it is a true positive for the test condition.
- If a legitimate integration produces the same pattern, the alert may be a false positive after investigation.
- If an attacker makes only four attempts in five minutes, the rule may not alert. That is a possible false negative for this detection logic, even if another detection identifies the behavior.

## Good tuning principles
1. Do not suppress an alert solely because it is noisy; identify why it fires.
2. Prefer narrow, documented exceptions over broad exclusions.
3. Add expiry or review dates to allowlist entries.
4. Preserve raw event data for investigation.
5. Track detection outcomes and tune using evidence.
6. Measure detection coverage as well as alert volume.

A low alert count does not necessarily mean a system is effective. It may indicate good tuning, but it may also indicate missing telemetry or rules that are too restrictive.
