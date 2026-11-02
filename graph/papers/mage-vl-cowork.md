---
id: paper:mage-vl-cowork
type: paper
title: 'Mage-VL-Cowork: A Full Training Recipe to Learn Hybrid Computer Use From Evolved Harnesses'
authors:
- 'Xiaoyi Zhang'
- 'Haoqing Wang'
- 'Xinjie Zhang'
- 'Xiang Ming'
- 'Xing Wang'
- 'Senqiao Yang'
- 'Kaichen Zhang'
- 'Zhaoyang Jia'
- 'Andong Tan'
- 'Xinjiang Wang'
- 'Jinghao Guo'
- 'Yifei Shen'
- 'Xiao Li'
- 'Peng Zhang'
- 'Xun Guo'
- 'Jiahao Li'
- 'Shicheng Zheng'
- 'Jinglu Wang'
- 'Zongyu Guo'
- 'Wenxuan Xie'
- 'Bin Li'
- 'Yan Lu'
year: 2026
month: 10
arxiv_id: '2610.40747'
url: https://arxiv.org/abs/2610.40747
methods:
- method:mage-vl-cowork
cites:
- paper:os-helix
- paper:recreationworld
tags:
- computer-use
- hybrid
- active
---

# Mage-VL-Cowork: A Full Training Recipe to Learn Hybrid Computer Use From Evolved Harnesses

## Abstract Summary
Mage-VL-Cowork is a 4B hybrid CUA trained through a five-stage midtraining/SFT/RL curriculum. Mage-CUA-Forge synthesizes 293,806 desktop and web tasks across 6,915 skills and cuts recurring per-task spend 82.6%. Teacher harnesses are evolved rather than distilled from a default teacher. Mage-VL-Cowork-4B reaches 66.0% on OSWorld-Verified.

## Key Contributions
1. Five-stage hybrid CUA recipe plus skill-conditioned task forge.

## Empirical Highlights
OSWorld-Verified 66.0% at 4B is not OSWorld 2.0 paper protocol. Code github.com/microsoft/Mage. Sibling of method:os-helix. Does not demote method:recreationworld or method:claude-computer-use.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.40747`
- Code: `https://github.com/microsoft/Mage` (`code_status: released`).
- Project: `https://microsoft.github.io/Mage`
