# TryHackMe Write-up — Pyramid of Pain

## Objective
Understand why some indicators of compromise are easier for adversaries to change than others.

## Levels
From lower to higher adversary pain: hash values, IP addresses, domain names, network/host artefacts, tools, and TTPs (tactics, techniques and procedures).

## Defensive Meaning
A hash is easy to change by modifying a file. Infrastructure can also be replaced. Detecting behaviour and TTPs can force an adversary to change more of their operation, although behavioural detections require context and careful tuning.

## Learning Reflection
Use multiple layers of indicators. Do not rely on a single hash or IP as a complete detection strategy.
