---
id: paper:automaster
type: paper
title: 'AutoMaster: Autonomous Post-Training by Making the Same Model a Better Teacher'
authors:
- Guoxin Chen
- Shuang Sun
- Fanzhe Meng
- Xinyu Tang
- Ruihua Song
- Wayne Xin Zhao
year: 2026
month: 11
arxiv_id: '2611.26510'
url: https://arxiv.org/abs/2611.26510
methods:
- method:automaster
cites: []
tags:
- sft
- skills
- agent
- automaster
---

# AutoMaster: Autonomous Post-Training by Making the Same Model a Better Teacher

## Abstract Summary
Skill-FT / AutoMaster collects teacher trajectories under a skill bank, then SFT the student on those traces. Skills stay in the train harness and are dropped at eval. Compared with vanilla SFT on 512 trajectories (3 epochs, lr 1e-5, batch 32) on Qwen3.5-4B/9B.

## Key Contributions
1. Skill-conditioned teacher rollouts as the SFT corpus.
2. Train-only skills; eval uses the target harness.
3. Terminal-Bench 2.1 / BrowseComp / Doc2Repo bake-off vs vanilla SFT.

## Empirical Highlights
Qwen3.5-4B/9B vs vanilla SFT: TB2.1 22.47→28.09 (+5.62) / 26.59→35.58 (+8.99); BrowseComp 43.24→46.13 (+2.88) / 46.85→51.53 (+4.68); Doc2Repo 32.30→33.72 (+1.42) / 36.05→40.79 (+4.74). 4B BrowseComp/Doc2Repo CIs include 0; 9B CIs are all positive.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.26510`
- Code: `https://github.com/RUCAIBox/AutoMaster`
