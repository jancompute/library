---
id: paper:turnwise
type: paper
title: 'Turns Matter: Advancing Streaming Video RL via Turn-Level Credit'
authors:
- Shuai Dong
- Kanghui Tian
- Linghan Chen
- Wenqi Shao
- Hongrui Wu
- Haowen Hou
- Yongfu Zhu
- Xuehui Wang
- Ziyue Wang
- Wenpu Liu
- Weichu Xie
- Yuqi Xu
- Congcong Wang
- Kaiwen Tuo
- Caoyuan Ma
- Taiqiang Wu
- Ji Zhao
- Wenzheng Chang
- Dianyi Wang
- Siyuan Wang
- Zhongyu Wei
- Yu Qiao
- Jiaqi Wang
year: 2026
month: 11
arxiv_id: '2611.06728'
url: https://arxiv.org/abs/2611.06728
methods:
- method:turnwise
cites:
- paper:orarl
- paper:framegrpo
tags:
- video-mllm
- streaming
- turn-credit
- active
---

# Turns Matter: Advancing Streaming Video RL via Turn-Level Credit

## Abstract Summary
TurnWise assigns remaining-return advantages from silence-completed prefixes and averages the GRPO loss at turn granularity. Trajectory-level GRPO otherwise credits later redundant replies for earlier successes.

## Key Contributions
1. Silence-completed prefix scoring without a critic or extra rollouts.
2. Turn-mean aggregation so wait and respond decisions share weight.

## Empirical Highlights
Best aggregates on ProactiveVQA, OVO-Timing, and StreamingBench with both Qwen backbones. 3B repetition 15.53→5.98. Does not retarget OraRL.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.06728`
- Code: announced in the paper header (`code_status: announced`); no URL found as of 2026-11-05.
