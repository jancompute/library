---
id: paper:statealign
type: paper
title: 'StateAlign: Internalizing State-Aware Decision-Making for Reliable Multi-Turn Tool Agents via Reinforcement Learning'
authors:
- Zhexi Lu
- Subhajit Chaudhury
- Tejaswini Pedapati
- Keerthiram Murugesan
- Lei Yu
year: 2026
month: 11
arxiv_id: '2611.16304'
url: https://arxiv.org/abs/2611.16304
methods:
- method:statealign
cites: []
tags:
- agentic-rl
- tool-use
- state-contrast
- active
---

# StateAlign: Internalizing State-Aware Decision-Making for Reliable Multi-Turn Tool Agents via Reinforcement Learning

## Abstract Summary
IBM / RPI. State-contrast RL for multi-turn tool agents. Qwen3-8B BFCL v4 multi-turn 45.5%→55.2%; no-tool hallucination 62.2%→56.1% vs outcome-only. Agents sometimes execute when they should ask, retrieve, or wait. Code `ZhexiLu/StateAlign` (`code_status: released`). Does not retarget SAO or CANOPY.

## Key Contributions
1. Contrast the current interaction state against a counterfactual so the policy internalizes when to call, ask, or wait.
2. Outcome-only RL can raise task reward while increasing tool hallucination; state contrast reduces that.
3. Evaluated on BFCL v4 multi-turn tool use.

## Empirical Highlights
Qwen3-8B BFCL v4 multi-turn 45.5%→55.2%. No-tool hallucination 62.2%→56.1% vs outcome-only. Distinct from CANOPY coverage and SAO async stragglers.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.16304`
- Code: `https://github.com/ZhexiLu/StateAlign` (`code_status: released`).
