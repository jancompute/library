---
id: paper:sign-law-entropy-rlvr
type: paper
title: 'A Sign Law for Entropy Drift under Sampler Mismatch in RLVR'
authors:
- 'Zhiyuan Wang'
- 'Jacob Steeves'
- 'Chang Liu'
year: 2026
month: 10
arxiv_id: '2610.34044'
url: https://arxiv.org/abs/2610.34044
methods:
- method:cispo
cites:
- paper:minimax-m1
tags:
- rlvr
- gotcha
- entropy
---

# A Sign Law for Entropy Drift under Sampler Mismatch in RLVR

## Abstract Summary
RLVR entropy rises or falls with choices that should be neutral, such as masking vs failing over-length responses. The cause is sampler mismatch: rollouts use top-k/top-p or a temperature the learner does not. A constant advantage shift then moves softmax entropy with a sign fixed by the sampler.

## Key Contributions
1. Sign law for entropy drift; not a CISPO replacement.

## Empirical Highlights
Positive advantage shifts sharpen under top-k, top-p, min-p, and temperatures below one, and flatten under flatter samplers. Token-level group RLVR makes the baseline-controlled drift equal the token-weighted net advantage.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.34044`
- Code: `none found (`code_status: none`).`
