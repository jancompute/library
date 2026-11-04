---
id: paper:loco
type: paper
title: 'LoCo: Local Continue-or-Conclude Preference for Shorter RLVR'
authors:
- 'Muyao Yuan'
- 'Liyan Xu'
- 'Weizhan Zhang'
- 'Muyan Jiao'
- 'Jiangnan Li'
- 'Jinchao Zhang'
- 'Jie Zhou'
year: 2026
month: 11
arxiv_id: '2611.04814'
url: https://arxiv.org/abs/2611.04814
methods:
- method:loco
cites:
- paper:minimax-m1
- paper:when2think
tags:
- rlvr
- length
- active
---

# LoCo: Local Continue-or-Conclude Preference for Shorter RLVR

## Abstract Summary
LoCo trains a local DPO continue-vs-conclude decision from frozen prefixes so RLVR traces stop earlier without swapping the Pass@1 loss. Sibling of When2Think / LSD.

## Key Contributions
1. Local DPO on continue-vs-conclude from frozen prefixes.
2. Large length cuts on math and code with a CISPO/GRPO host.

## Empirical Highlights
Math length −41.7% to −45.4%; code −23.4% to −36.3%.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.04814`
- Code: `https://github.com/MuyaoYuan/LoCo` (`code_status: released`).
