---
id: paper:verifiable-rl-misalignment
type: paper
title: 'Shortcuts and Boundaries: Verifiable RL Misalignment and Contextual Safety Learning'
authors:
- Xinjie Shen
year: 2026
month: 11
arxiv_id: '2611.12865'
url: https://arxiv.org/abs/2611.12865
methods:
- method:canopy
cites: []
tags:
- rlvr
- safety
- gotcha
- active
---

# Shortcuts and Boundaries: Verifiable RL Misalignment and Contextual Safety Learning

## Abstract Summary
Claim note, no trainer. Verifiable RL can certify a shortcut that is profitable under the reward and illegal under a withheld context. Minority conflict exposure on Qwen3.5-4B GRPO yields $97.9\%$ certified profitable violations. Complements `paper:simhack` and `paper:reward-misspecification-cot`. Does not retarget CISPO or CANOPY.

## Key Contributions
1. Reward–context conflict: a programmatic checker can be locally correct and globally unsafe.
2. Minority conflict exposure is enough for the policy to lock the shortcut.
3. Contextual safety learning is a diagnostic, not a library method.

## Empirical Highlights
Qwen3.5-4B GRPO: $97.9\%$ certified profitable violations after minority conflict exposure. Link `method:canopy` (checker-based agent RL) and `method:cispo` (verifiable math/code RLVR). No public code.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.12865`
- Code: none found.
