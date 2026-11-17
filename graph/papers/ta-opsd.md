---
id: paper:ta-opsd
type: paper
title: 'Learning When to Continue and When to Stop: Termination-Aware OPSD'
authors:
- Chaoqun He
- Wannian Yi
- Changyi Sun
- Chaojun Xiao
- Lijie Wen
year: 2026
month: 11
arxiv_id: '2611.19925'
url: https://arxiv.org/abs/2611.19925
methods:
- method:ta-opsd
cites: []
tags:
- opsd
- termination
- privileged-teacher
- active
---

# Learning When to Continue and When to Stop: Termination-Aware OPSD

## Abstract Summary
Vanilla OPSD has a termination mismatch: premature EOS versus repetition-driven over-generation. Teacher-student EOS discrepancy grows; length-capped traces are often unproductive repetition. TA-OPSD adds Stop/Continue Distillation and Repetition-Aware Unlikelihood. Qwen3 1.7B/4B/8B math: beats OPSD at all three scales. Distinct from `method:opd-eos`. Code gtbxdf4/TA-OPSD. Does not retarget VISTA.

## Key Contributions
1. Documents growing teacher-student EOS discrepancy under OPSD.
2. Stop/Continue Distillation for premature termination.
3. Repetition-Aware Unlikelihood on failed student traces.

## Empirical Highlights
Qwen3 1.7B/4B/8B: consistently outperforms OPSD. Ablations split the two failure modes.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.19925`
- Code: `https://github.com/gtbxdf4/TA-OPSD` (`code_status: released`).
