---
id: paper:coverage-collapse-reference-resets
type: paper
title: 'A Theory of Policy Optimization in Post-Training: Coverage Collapse and Reference Resets'
authors:
- Audrey Huang
- Nan Jiang
- Sham M. Kakade
- Sadhika Malladi
- Akshay Krishnamurthy
- Dylan J. Foster
year: 2026
month: 11
arxiv_id: '2611.14467'
url: https://arxiv.org/abs/2611.14467
methods:
- method:cispo
cites:
- paper:minimax-m1
tags:
- rlvr
- coverage
- reference-reset
- claim-note
---

# A Theory of Policy Optimization in Post-Training: Coverage Collapse and Reference Resets

## Abstract Summary
Claim note, no new method. REINFORCE / PPO / GRPO can drive the probability of optimal responses to near zero even as reward improves (coverage collapse), including under KL to a fixed base. Approximate Policy Mirror Descent (APMD) resets the KL reference to the latest policy and is coverage-preserving for stylized PPO/GRPO and Kimi-style squared-loss algorithms. Complements `paper:rlvr-no-free-lunch` / `paper:sharpening-tax` / `method:es-reasoning`. Does not retarget CISPO. No public code. APMD is not a library method.

## Key Contributions
1. Coverage collapse: reward up, mass on optimal responses down, even with exact gradients and a KL to the base.
2. Reference resets (APMD) restore coverage-preserving convergence.
3. Clipping limits the statistical cost of large IS weights; it is not itself the coverage fix.

## Empirical Highlights
Theory card. Pair with ES-reasoning (Pass@K first hop) and the no-free-lunch / sharpening-tax notes. ProRL / DeepSeek-style reference resets are the practical intervention. Does not retarget CISPO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.14467`
- Code: none found (`code_status: none`).
