---
id: paper:specal
type: paper
title: 'SpeCal: Spectral Calibration for Unsupervised RLVR'
authors:
- Kai Tang
- Xing Zheng
- Haobo Wang
- Guangcheng Zhu
- Shenzhi Yang
- Zhengqing Zang
- Yingfan Ma
- Cheng Peng
- Bowen Song
- Weiqiang Wang
year: 2026
month: 11
arxiv_id: '2611.20691'
url: https://arxiv.org/abs/2611.20691
methods:
- method:specal
cites: []
tags:
- rlvr
- unsupervised
- spectral
- active
---

# SpeCal: Spectral Calibration for Unsupervised RLVR

## Abstract Summary
Unsupervised RLVR derives scalar rewards from the model's own rollouts, but endpoint statistics miss whether the rollout representations form a reliable learning structure. SpeCal calibrates group and rollout advantages from hidden-state spectra (spectral mass, Gaussian band-pass on entropy-based effective rank, leave-one-out spectral support) without redefining the unlabeled reward. KDD 2027. No public code. Does not retarget u-OPSD.

## Key Contributions
1. Hidden-state spectra as a reliability view for unlabeled RLVR groups.
2. Group-level spectral mass plus Gaussian band-pass on effective rank.
3. Rollout-level leave-one-out spectral support used as an advantage gate.

## Empirical Highlights
KDD 2027 accepted. Calibrates existing unlabeled advantages rather than replacing the reward.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.20691`
- Code: none found (`code_status: none`).
