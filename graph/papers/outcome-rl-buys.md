---
id: paper:outcome-rl-buys
type: paper
title: 'What Outcome RL Buys: Finishing, Reliability, Rarely Reach'
authors:
- 'Shan Yang'
year: 2026
month: 10
arxiv_id: '2610.34894'
url: https://arxiv.org/abs/2610.34894
methods:
- method:cispo
cites:
- paper:what-rl-brings
- paper:minimax-m1
tags:
- rlvr
- gotcha
---

# What Outcome RL Buys: Finishing, Reliability, Rarely Reach

## Abstract Summary
Pass@1 under a token budget mixes finishing, reliability, and reach. On 20 released RL models (1.5B–32B) vs their thinking bases, finishing is 82% of the change at 4k/8k where the base hits the cap; once the base finishes, the rest is reliability; reach adds at most 2.1 pp. Complements paper:what-rl-brings (sparse decision replace), different split.

## Key Contributions
1. Budget-aware finishing / reliability / reach split of outcome-RL pass@1; not a CISPO replacement.

## Empirical Highlights
20 released pairs on physics and MATH-500 / competition math. Of 144 physics lone-wins, 3.5% hold up when resampled or read. Small 8B run: new-problem gain is finishing, reliability flat. Compare a recipe with its base at or above its training cap. Does not retarget CISPO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.34894`
- Code: `https://github.com/shanyang-me/outcome-rl-buys` (`code_status: released`). Project: `https://shanyang.me/what-outcome-rl-buys/`.
