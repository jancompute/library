---
id: paper:best-of-depth
type: paper
title: 'Best-of-Depth: Train Every Loop Count as a Candidate'
authors:
- 'Shota Takashiro'
- 'Takeshi Kojima'
- 'Masanori Koyama'
- 'Kohei Hayashi'
- 'Yusuke Iwasawa'
year: 2026
month: 11
arxiv_id: '2611.04663'
url: https://arxiv.org/abs/2611.04663
methods:
- method:best-of-depth
cites:
- paper:elr
tags:
- architecture
- looped-lm
- active
---

# Best-of-Depth: Train Every Loop Count as a Candidate

## Abstract Summary
Best-of-Depth trains all loop depths as a candidate set rather than supervising only the final depth. N-Queens coverage 91.03% vs 45.75% at final-depth training.

## Key Contributions
1. Treat every loop count as a train-time candidate, not just the last loop.

## Empirical Highlights
N-Queens coverage 91.03% vs 45.75% final-depth.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.04663`
- Code: none found (`code_status: none`).
