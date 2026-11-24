---
id: paper:vopd
type: paper
title: Verifiable On-Policy Distillation
authors:
- Juntong Shi
- Stefano Ermon
- Jure Leskovec
- Minkai Xu
year: 2026
month: 11
arxiv_id: '2611.30325'
url: https://arxiv.org/abs/2611.30325
methods:
- method:vopd
cites: []
tags:
- distillation
- opd
- rlvr
- verifier
---

# Verifiable On-Policy Distillation

## Abstract Summary
VOPD extrapolates the OPD teacher target with a group-relative verifier advantage on student prefixes, using a frozen reference. Distinct from OPDVR (ReLU correctness gating of sampled-token OPD). Code juntongshi48/VOPD announced, not released.

## Key Contributions
1. Verifier-grounded dense teacher extrapolation at \(\lambda=0.25\) with a frozen reference.
2. Same-size 4B student exceeds both vanilla OPD and the RL teacher average.
3. Strong-to-weak 4B→1.7B still leads OPD / ExOPD / OPD+GRPO.

## Empirical Highlights
Qwen3-4B same-size eight-bench avg 66.38 vs OPD 64.71 / ExOPD 65.25 / teacher 64.16. Qwen3-1.7B 53.32 vs OPD 50.88 / ExOPD 52.34. \(\lambda=0.25\) best; larger \(\lambda\) degrades.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.30325`
- Code: `https://github.com/juntongshi48/VOPD` (`code_status: announced` as of 2026-11-24)
