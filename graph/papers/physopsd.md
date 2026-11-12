---
id: paper:physopsd
type: paper
title: 'PhysOPSD: Code as Privilege for Physically Plausible Video Generation'
authors:
- Harold Haodong Chen
- Rui Peng
- Lingteng Qiu
- Kejie Qiu
- Chao Xu
- Zilong Dong
year: 2026
month: 11
arxiv_id: '2611.12411'
url: https://arxiv.org/abs/2611.12411
methods:
- method:physopsd
cites: []
tags:
- diffusion
- opsd
- video
- active
---

# PhysOPSD: Code as Privilege for Physically Plausible Video Generation

## Abstract Summary
Video OPSD with executable code as privileged physical context. PhysOPSD-Engine compiles scene code into a privileged teacher; PhysOPSD-3K is the 3K-sample training set. Dual-level privilege (global + token-wise) plus shared-noise variation. Distinct from text-to-image DiffusionOPSD / Self-OPD. HF Daily leftover below the 11-11 watermark. Code aigc3d/PhysOPSD released.

## Key Contributions
1. Code-as-privilege: teacher sees compiled physical context, student does not.
2. Dual-level OPSD (global + token-wise) with shared-noise variation.
3. 3K samples vs SFT 80K / offline RL 21K at matched physics quality.

## Empirical Highlights
UniVideo 13B / OmniWeaving 8.3B VideoPhy-2 overall $+4.2$ / $+4.1$, PhyGround $+1.6$ / $+3.4$. VBench UniVideo $83.5\to 84.0$. Does not retarget DiffusionOPSD or VISTA.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.12411`
- Code: `https://github.com/aigc3d/PhysOPSD` (`code_status: released`).
- Site: `https://haroldchen19.github.io/PhysOPSD-site/`
