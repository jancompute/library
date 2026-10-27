---
id: paper:proas
type: paper
title: 'ProAS: A Progress-Aware Advantage Shaping Framework for Multi-Turn Agentic Reinforcement Learning'
authors:
- 'Bowen Ding'
- 'Mingda Wan'
- 'Yuhan Chen'
- 'Jiyao Yuan'
- 'Qi Zhu'
- 'Futing Wang'
- 'Heyuan Deng'
- 'Fei Mi'
- 'Lifeng Shang'
- 'Tao Lin'
year: 2026
month: 10
arxiv_id: '2610.18683'
url: https://arxiv.org/abs/2610.18683
methods:
- method:proas
cites:
- paper:canopy
- paper:sao
tags:
- rlvr
- agentic
- active
---

# ProAS: A Progress-Aware Advantage Shaping Framework for Multi-Turn Agentic Reinforcement Learning

## Abstract Summary
Critic-free group RL broadcasts one trajectory advantage to every action, which reinforces structurally unreasonable steps in winners. ProAS shapes advantages with a growing Agentic Reference Graph via MUI and APR. Previously SKIPPED 2026-10-14; ingested after HF Daily plus released code.

## Key Contributions
1. ProAS as an active plug-in on task:outcome-only-long-horizon-agent-rl.

## Empirical Highlights
Qwen2.5-1.5B/7B-Instruct ALFWorld 91.9/94.3 and WebShop 66.7/70.8; up to 2.44x faster convergence. Code LINs-lab/ProAS.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.18683`
- Code: `https://github.com/LINs-lab/ProAS (`code_status: released`).`
