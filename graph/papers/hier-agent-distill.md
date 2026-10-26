---
id: paper:hier-agent-distill
type: paper
title: 'Beyond On-Policy vs. Off-Policy: At What Level Should LLM Agent Distillation Follow the Student?'
authors:
- 'Ya Gao'
- 'Zhengtao Zou'
- 'Pekka Marttinen'
year: 2026
month: 10
arxiv_id: '2610.31918'
url: https://arxiv.org/abs/2610.31918
methods:
- method:opd
cites:
- paper:opd
tags:
- distillation
- gotcha
- agents
---

# Beyond On-Policy vs. Off-Policy

## Abstract Summary
Agent distillation is hierarchical: the policy that induces the interaction history need not be the policy that writes the token prefix. On-policy vs off-policy is the wrong binary.

## Key Contributions
1. Hierarchical on/off-policy for agent distill; not a matching default.

## Empirical Highlights
- Does not retarget OPD or CANOPY. Choose the follow-the-student level explicitly.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.31918`
- Code: `none found` (`code_status: none`).
