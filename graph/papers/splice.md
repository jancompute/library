---
id: paper:splice
type: paper
title: 'SPLICE: Salvaging All-Fail Groups by Splicing Bounded Options into Learner Continuations'
authors:
- Haowen Hou
- Yicheng Liu
- Zhen Huang
- Jiaqi Wang
year: 2026
month: 11
arxiv_id: '2611.34777'
url: https://arxiv.org/abs/2611.34777
methods:
- method:splice
cites: []
tags:
- rl-alignment
- all-fail
- agentic
---

# SPLICE: Salvaging All-Fail Groups by Splicing Bounded Options into Learner Continuations

## Abstract Summary
When a GRPO group is all-fail, a frozen proposal model splices a bounded set of options at a branch point; the learner continues; a return-weighted local target updates the policy. Distinct from GRAFT (peer trajectory exchange), Harness-S (sibling-harness re-roll), PICO (joint expert-guided decoding), and VeriGate (process-supervision gate).

## Key Contributions
1. Branch-point splice of bounded proposal options into learner-conditioned continuations.
2. Return-weighted local target instead of swapping the whole trajectory.
3. SWE-bench Verified and BrowseComp-Plus vs GRPO; graduation on initially failed SWE.

## Empirical Highlights
+2.8–9.8pp vs GRPO on SWE-Verified and BrowseComp-Plus. +10.8pp graduation on initially failed SWE. No public GitHub as of 2026-11-26.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.34777`
- Code: none found as of 2026-11-26
