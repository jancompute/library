---
id: paper:credit-helps-hurts
type: paper
title: 'When Fine-Grained Credit Assignment Helps and Hurts: Multimodal Agentic Reinforcement Learning through Video Editing'
authors:
- 'Lei Zhao'
- 'Zongheng Cao'
- 'Xinyu Hu'
year: 2026
month: 10
arxiv_id: '2610.35497'
url: https://arxiv.org/abs/2610.35497
methods:
- method:canopy
- method:draco
cites:
- paper:canopy
- paper:draco
tags:
- rlvr
- gotcha
- agentic
---

# When Fine-Grained Credit Assignment Helps and Hurts: Multimodal Agentic Reinforcement Learning through Video Editing

## Abstract Summary
Fine-grained process credit is not uniformly better than outcome-only GRPO. On movie-trailer editing, decaying process rewards help most on Fine Cut (45.4% relative over outcome-only GRPO at >60 turns) and can fail to help on shorter-horizon types averaging 30-40 turns.

## Key Contributions
1. Process vs outcome credit depends on horizon; not a CANOPY replacement.

## Empirical Highlights
Project https://leizhao7.github.io/videoedit/. Does not retarget CANOPY or DRACO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.35497`
- Code: `https://leizhao7.github.io/videoedit/ (`code_status: announced`).`
