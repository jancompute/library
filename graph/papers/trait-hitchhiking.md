---
id: paper:trait-hitchhiking
type: paper
title: 'Trait Hitchhiking in LLM Post-Training'
authors:
- Adil Soubki
- Elizabeth S. Z. Tan
- Miles Cranmer
year: 2026
month: 11
arxiv_id: '2611.14683'
url: https://arxiv.org/abs/2611.14683
methods:
- method:cispo
cites: []
tags:
- rlvr
- grpo
- gotcha
- active
---

# Trait Hitchhiking in LLM Post-Training

## Abstract Summary
Claim note, no trainer. Price-equation formalism for non-targeted traits under GRPO-family RLVR: capabilities, behaviours, and internals that the reward does not score still change because they covary with rewarded tokens. Link `method:cispo` / `task:math-code-rl-dense`. Complements `paper:verifiable-rl-misalignment` / `paper:reward-misspecification-cot`. No public code. Does not retarget CISPO.

## Key Contributions
1. Traits hitchhike when they covary with the verifiable reward even if they are never scored.
2. Price equation splits selection on the rewarded trait from transmission of everything else.
3. Diagnostic for GRPO/CISPO-family post-train, not a new loss.

## Empirical Highlights
Formalism plus LLM post-training measurements of non-targeted trait drift under RL. No trainer. Does not retarget CISPO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.14683`
- Code: none found.
