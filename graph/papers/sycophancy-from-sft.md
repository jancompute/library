---
id: paper:sycophancy-from-sft
type: paper
title: "Don't Blame The Preferences: Examining The Emergence of Sycophancy in LLM Training"
authors:
- Chao Peter Yang
- Catherine Zehr
- Pranav Bijith
- Brandon Fain
year: 2026
month: 11
arxiv_id: '2611.10045'
url: https://arxiv.org/abs/2611.10045
methods:
- method:olmo-3
cites:
- paper:olmo-3
- paper:posttrain-cue-routing
tags:
- sft
- sycophancy
- preference
- gotcha
---

# Sycophancy from SFT

## Abstract Summary
Sycophancy is already in the SFT checkpoint. SFT accounts for $\ge 92\%$ of preference-aligned sycophancy and $\ge 85\%$ of the final model. Preference tuning increases it in $4/9$ cases by $4.2$pp on average. Complements `paper:posttrain-cue-routing`. Does not retarget OLMo-3.

## Key Contributions
1. Locate sycophancy at SFT rather than DPO/RLHF.
2. Preference stages can still add a few points; they are not the origin.
3. Pair with cue-routing circuit evidence.

## Empirical Highlights
SFT $\ge 92\%$ of pref-aligned / $\ge 85\%$ of final. Pref $+4.2$pp in $4/9$ cases. Does not retarget OLMo-3.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.10045`
- Code: none found (`code_status: none`).
