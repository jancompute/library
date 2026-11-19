---
id: paper:copd
type: paper
title: Communicative On-Policy Distillation
authors:
- Lirui Luo
- Kelong Mao
- Xinwei Yang
- Rongqing Li
- Luyu Chen
- Kieran Wong
- Yudong Guo
- Xinrui Wang
- Jiayin Zhu
- Gu Simiu
- Sulong Xu
- Cong Fang
year: 2026
month: 11
arxiv_id: '2611.23673'
url: https://arxiv.org/abs/2611.23673
methods:
- method:copd
cites: []
tags:
- opd
- black-box
- agentic
- camg-ii
- active
---

# Communicative On-Policy Distillation

## Abstract Summary
COPD distills a black-box teacher that does not expose logits. The student decides when to consult in natural language, then successful consultations become privileged references for adviser-free on-policy self-distillation plus task-reward RL. On CAMG-II, COPD-4B 45.3→59.8 vs ActionOPD 51.2 (2.46× the ActionOPD gain); COPD-9B 54.2→61.3 vs ActionOPD 54.6. Transfer: TB 2.1 / SWE-Bench Pro V2 COPD-4B 23.1/11.2→28.0/16.5, COPD-9B 23.1/23.1→33.0/27.5 (avg 30.3 vs Qwen3.5-35B-A3B 30.6). Distinct from OPD, ActionOPD, Bridged Self-Distill, Stepwise Querying, CAMP-II. No public train code (`code_status: none`; project liruiluo.github.io/communicative-opsd/). Does not retarget OPD or CANOPY.

## Key Contributions
1. Student-initiated open-ended NL consult of a black-box teacher, no templates or intervention schedule.
2. Privileged OPSD on adviser-free student rollouts plus task-reward RL.
3. CAMG-II adviser-free gains transfer to Terminal-Bench 2.1 and SWE-Bench Pro V2.

## Empirical Highlights
CAMG-II 4B 45.3→59.8 vs ActionOPD 51.2; 9B 54.2→61.3 vs ActionOPD 54.6. TB 2.1 / SWE-Bench Pro V2 COPD-9B avg 30.3 vs 35B-A3B 30.6.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.23673`
- Project: `https://liruiluo.github.io/communicative-opsd/`
- Code: `none found` (`code_status: none`).
