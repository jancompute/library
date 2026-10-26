---
id: paper:openattention
type: paper
title: 'OpenAttention: One Percent Is Enough with Tail Proxies'
authors:
- 'Hyunwoo Yu'
- 'Jongbeom Lee'
- 'Hyunbin Kim'
- 'Sungjun Park'
- 'Jaemin Choi'
- 'Jincheol Yang'
- 'Seunghun Moon'
- 'Bongjoon Hyun'
- 'Kyomin Sohn'
- 'Kyeongbo Kong'
- 'Suk-Ju Kang'
year: 2026
month: 10
arxiv_id: '2610.30951'
url: https://arxiv.org/abs/2610.30951
methods:
- method:openattention
cites:
- paper:sas
tags:
- sparse-attention
- active
---

# OpenAttention

## Abstract Summary
Sparse attention that discards or samples the unread tail fails at 5% reads and below. OpenAttention folds the tail into one proxy token.

## Key Contributions
1. OpenAttention as an active plug-in on task:posttrain-attention-sparsification.

## Empirical Highlights
- 1% reads with a tail proxy. Does not retarget method:sas.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.30951`
- Code: `https://github.com/hyunwoo137/OpenAttention` (`code_status: released`).
