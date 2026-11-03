---
id: paper:fade
type: paper
title: 'FADE: Factored Ability--Difficulty Filtering for Online RLVR Scheduling'
authors:
- 'Tomas Duncun'
- 'Jonah Ellison'
- 'Mateo Ruiz'
- 'Hanae Fujita'
- 'Ingrid Solberg'
year: 2026
month: 11
arxiv_id: '2611.03625'
url: https://arxiv.org/abs/2611.03625
methods:
- method:fade
cites:
- paper:minimax-m1
- paper:thinkprior
- paper:ngu
- paper:adaroll-grpo
tags:
- rlvr
- scheduling
- active
---

# FADE: Factored Ability--Difficulty Filtering for Online RLVR Scheduling

## Abstract Summary
All-pass and all-fail RLVR groups waste budget. Per-prompt pass-rate trackers entangle fast-moving policy skill with slow item difficulty. FADE is a bilinear state-space filter: a whitened K-dimensional skill loading times a fast ability vector, minus a slow item intercept, updated with Polya-Gamma / Woodbury so competence shifts transfer to unseen prompts that share those skills.

## Key Contributions
1. Factored ability-difficulty RLVR scheduler that does not scramble prompt order.

## Empirical Highlights
Closed-form utility from posterior mean and variance; closed-form rank-K ability update per minibatch. Distinct from ThinkPrior / NGU / AdaRoll-GRPO / EnvSched.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.03625`
- Code: none found (`code_status: none`).
