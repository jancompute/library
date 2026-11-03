---
id: paper:cua-master
type: paper
title: 'CUA-Master: Scaling Computer-use Agents through Open-World Recursive Improvements'
authors:
- 'Xinlei Yu'
- 'Gen Li'
- 'Ji Zhao'
- 'Zhangquan Chen'
- 'Congcong Wang'
- 'Shuai Dong'
- 'Zelin Peng'
- 'Yuqi Xu'
- 'Hongrui Wu'
- 'Kaiwen Tuo'
- 'Cheng Yang'
- 'Kaituo Feng'
- 'Yifan Wu'
- 'Jiayi Zhang'
- 'Dongming Wu'
- 'Wenqi Shao'
- 'Jiaqi Wang'
- 'Xiangyu Yue'
year: 2026
month: 11
arxiv_id: '2611.03126'
url: https://arxiv.org/abs/2611.03126
methods:
- method:cua-master
cites:
- paper:recreationworld
- paper:opengcua
- paper:os-helix
- paper:mage-vl-cowork
tags:
- cua
- hybrid
- active
---

# CUA-Master: Scaling Computer-use Agents through Open-World Recursive Improvements

## Abstract Summary
CUA-Master is a nested double-loop: an outer world-data-model flywheel and an inner open-world seeding plus autocatalytic task synthesis, with snapshot-rollback retry in real environments. 27B scores 80.2 on OSWorld Verified and 36.9 on OSWorld 2.0. That 36.9 is not the library OSWorld 2.0 paper-protocol ranking (Claude 20.6% binary uses a different protocol and scale).

## Key Contributions
1. Nested open-world flywheel for hybrid GUI+CLI computer-use training.

## Empirical Highlights
CUA-Master-27B 80.2 OSWorld Verified / 36.9 OSWorld 2.0. Do not retarget Claude computer-use. Code xlyu0106/CUA-Master.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.03126`
- Code: `https://github.com/xlyu0106/CUA-Master` (`code_status: released`).
