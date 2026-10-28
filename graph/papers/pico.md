---
id: paper:pico
type: paper
title: 'When All Rollouts Fail: Policy-Compatible Joint Decoding for Hard-Problem Reasoning'
authors:
- 'Zehao Wang'
- 'Hanzhu Chen'
- 'Runquan Gui'
- 'Zhe Wang'
- 'Lin Yang'
year: 2026
month: 10
arxiv_id: '2610.36849'
url: https://arxiv.org/abs/2610.36849
methods:
- method:pico
cites:
- paper:verigate
- paper:minimax-m1
tags:
- rlvr
- all-fail
- active
---

# When All Rollouts Fail: Policy-Compatible Joint Decoding for Hard-Problem Reasoning

## Abstract Summary
All-fail RLVR groups give zero advantage. Expert clones are off-policy. PICO jointly decodes expert-guided, student-compatible traces under a divergence budget and trains them with mixed-behavior IS.

## Key Contributions
1. PICO as an active silent-group plug-in on task:all-zero-verifier-groups.

## Empirical Highlights
Outperforms standard RLVR and prior off-policy baselines on reasoning and agentic benches. Does not retarget method:verigate or method:cispo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.36849`
- Code: `none found (`code_status: none`).`
