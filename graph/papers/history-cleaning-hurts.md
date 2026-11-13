---
id: paper:history-cleaning-hurts
type: paper
title: "Cleaning an Agent's History Hurts When the World Still Holds the Error"
authors:
- Egor Pakhomov
- Anurag Koul
- Hongjun Liu
- Bo Pang
- Shafiq Joty
- Erik Nijkamp
year: 2026
month: 11
arxiv_id: '2611.14654'
url: https://arxiv.org/abs/2611.14654
methods:
- method:ace
cites: []
tags:
- agent-memory
- gotcha
- active
---

# Cleaning an Agent's History Hurts When the World Still Holds the Error

## Abstract Summary
Claim note, no trainer. After a wrong write, a truthful note raises recovery 51%→66%; a completed-action rewrite of the same value drops 50%→44%. Cleaning the history at a fixed world, where showing a corrected step and saying it is done move together, is the confound. Link `method:ace` / `task:agent-memory`. Complements `paper:memory-tax` / `paper:luck-carrying-lessons` / `method:wikitrace`. Does not retarget ACE.

## Key Contributions
1. Correct content can help or hurt depending on whether the world still holds the error.
2. A truthful note of the mistake aids recovery; rewriting the step as completed hides the mismatch.
3. History compaction / repair / handoff is not a free cleanup.

## Empirical Highlights
Truthful note 51%→66% recovery; completed-action rewrite 50%→44%. Same correct value, opposite sign. No public code.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.14654`
- Code: none found.
