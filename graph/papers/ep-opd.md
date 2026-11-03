---
id: paper:ep-opd
type: paper
title: 'Better Answers, Weaker Evidence Control: Evidence Bypass in On-Policy Distillation'
authors:
- 'Ruoran Xu'
- 'Yilun Zhao'
- 'Ziyu Chen'
- 'Xiaoqiang kang'
- 'Arman Cohan'
year: 2026
month: 11
arxiv_id: '2611.01967'
url: https://arxiv.org/abs/2611.01967
methods:
- method:ep-opd
cites:
- paper:opd
tags:
- opd
- evidence
- active
---

# Better Answers, Weaker Evidence Control: Evidence Bypass in On-Policy Distillation

## Abstract Summary
OPD can raise original-document accuracy while weakening evidence control. On QASPER with Qwen3-4B, OPD +3.4 original accuracy, -5.3 counterfactual, +15.7 bypass. Evidence-Paired OPD (EP-OPD) supervises matched documents that support different answers plus an answer-level margin. Recovers 54-66% of OPD's counterfactual-accuracy loss while keeping 80-85% of original-document gain.

## Key Contributions
1. Paired-document OPD against evidence bypass.

## Empirical Highlights
QASPER Qwen3-4B: OPD +3.4 / -5.3 / +15.7 bypass; EP-OPD recovers 54-66% of the counterfactual loss while keeping 80-85% of original-doc gain. Code github.com/RuoranXu/EP-OPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.01967`
- Code: `https://github.com/RuoranXu/EP-OPD` (`code_status: released`).
