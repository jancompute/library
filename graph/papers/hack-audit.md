---
id: paper:hack-audit
type: paper
title: 'Audit Where Hacks Pay: Budgeted Strong-Verifier Audits Against Reward Hacking in GRPO'
authors:
- 'Shurun Li'
- 'Michael Hua Wang'
- 'Haibo Zeng'
- 'Long Wang'
year: 2026
month: 10
arxiv_id: '2610.35716'
url: https://arxiv.org/abs/2610.35716
methods:
- method:hack-audit
cites:
- paper:minimax-m1
tags:
- rlvr
- active
---

# Audit Where Hacks Pay: Budgeted Strong-Verifier Audits Against Reward Hacking in GRPO

## Abstract Summary
Cheap unit-test rewards can be hacked; a strong verifier is too expensive for every rollout. Low-pass budgeted group audits (LB) spend the strong-check budget on groups with the fewest weak passes and reflect a caught hack about the failure reward.

## Key Contributions
1. Hack-audit as an active plug-in on task:math-code-rl-dense.

## Empirical Highlights
Frozen-panel mass sign predicted hacking suppression in 33/39 runs (13/16 preregistered). LeetCode and Countdown-Code: LB drives hacking near zero; random audits with the same budget do not. Does not retarget method:cispo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.35716`
- Code: `none found (`code_status: none`).`
