---
id: paper:harness-s
type: paper
title: 'Harness-S: Learning from Sibling Harnesses for Generalizable Agent Training'
authors:
- Kangning Zhang
- Wenxiang Jiao
- Bowen Fang
- Shuai Shao
- Jiachen Zhu
- Rong Shan
- Shijian Wang
- Hao Wang
- Yuan Lu
- Weiwen Liu
- Weinan Zhang
year: 2026
month: 11
arxiv_id: '2611.04277'
url: https://arxiv.org/abs/2611.04277
methods:
- method:harness-s
cites:
- paper:harnessflow
- paper:coharl
- paper:graft
- paper:canopy
- paper:harness-zero
tags:
- agents
- harness
- grpo
- active
---

# Harness-S: Learning from Sibling Harnesses for Generalizable Agent Training

## Abstract Summary
Harness-S freezes a sibling-harness pool during policy GRPO and rescues all-fail groups by re-rolling the same policy under a rank-1 sibling. Accepted replacements keep source advantages; the trained policy is then evaluated under the original $H_0$. Distinct from HarnessFlow (MCTS search), CoHARL (population co-evolution while the policy trains), GRAFT (peer-model traces), and Harness-Zero (SFT into a fixed action space).

## Key Contributions
1. Sibling-harness rescue of silent GRPO groups without editing the target harness during the policy update.
2. Transfer back to $H_0$: Qwen3.5-4B AppWorld Pass@3 / Avg@3 $67.56\pm1.87$ / $56.87\pm1.47$ vs GRPO $60.31$ / $48.98$ and GRPO+$H_0$-rescue $61.83$ / $51.91$.
3. Rank-1 routing after training: 4B $68.32$ / $61.45$; 9B $H_0$ $72.52\pm1.65$ / $62.34\pm1.28$ vs GRPO $64.89$ / $53.31$.

## Empirical Highlights
Table 1, Qwen3.5-4B/9B, AppWorld / SWE-Gym / DBBench. Routed 4B beats 9B GRPO+$H_0$-rescue on AppWorld Avg@3. Does not retarget omp2, CANOPY, or GRAFT.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.04277`
- Code: `https://github.com/DeepExperience/Harness-S` (`code_status: released`).
