---
id: paper:ngramrl
type: paper
title: 'NgramRL: Accelerating RL Post-Training for Structured Generation via Rollout-Aware N-gram Speculative Decoding'
authors:
- 'Nilesh Prasad Pandey'
- 'Jangseon Park'
- 'Jason Kong'
- 'Onat Gungor'
- 'Tajana Rosing'
year: 2026
month: 10
arxiv_id: '2610.32881'
url: https://arxiv.org/abs/2610.32881
methods:
- method:ngramrl
cites:
- paper:miles
- paper:uno
tags:
- rl
- speculative-decoding
- active
---

# NgramRL

## Abstract Summary
RL post-train is rollout-bound. Learned drafters eat memory and drift. NgramRL uses rollout-aware n-gram speculation for structured generation.

## Key Contributions
1. NgramRL as an active plug-in on task:frontier-rl-posttrain-stack.

## Empirical Highlights
- Model-free n-gram speculation for RL rollouts. Does not retarget method:miles or method:uno.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.32881`
- Code: `none found` (`code_status: none`).
