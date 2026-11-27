---
id: paper:maco-rl
type: paper
title: 'Maco-RL: Quota MixRL and Tri-Buffer Sampling for Agentic Continual Skill Add'
authors:
- Jiacheng Zhang
- Qixing Zhou
- Haiyang Wang
- Qipeng Gu
- Shuzhe Wu
- Feiyang Pan
- Lue Fan
- Dandan Tu
- Zhaoxiang Zhang
year: 2026
month: 11
arxiv_id: '2611.34703'
url: https://arxiv.org/abs/2611.34703
methods:
- method:maco-rl
cites:
- paper:sao
- paper:aclarena
- paper:category-aware-swe-experts
tags:
- rl-alignment
- agentic
- mixrl
- active
---

# Maco-RL: Quota MixRL and Tri-Buffer Sampling for Agentic Continual Skill Add

## Abstract Summary
Continual MixRL on a live coding-agent host forgets old skills when new environments arrive. Maco-RL keeps a quota MixRL update (Frontier / Reinforcement / History) plus Tri-Buffer Sampling of on-policy rollouts. TMax excludes already-solved tasks; Claw is uniform partial credit. Distinct from SAO (async straggler replay), ACLArena (offline replay + routed LoRA experts), and Category-Aware SWE Experts.

## Key Contributions
1. Quota MixRL: 20/60/20 Frontier / Reinforcement / History per update, not uniform replay.
2. Tri-Buffer Sampling from the current group's success counts (0 / mixed / all).
3. Two-stage skill add on Qwen3.5-27B then Qwen3.8-27B under verl + RLOO.

## Empirical Highlights
Qwen3.5-27B overall 43.6 → Maco-RL S1 54.2 → S2 60.1. Maco-RL-3.8 overall 67.0 vs Qwen3.8-27B 61.4. Table 1 cells (SWE-Verified / TB2.1 / GAIA2 / xbench-DeepSearch / HLE / BrowseComp / overall): Qwen3.5-27B 60.2/12.0/40.5/67.4/3.0/37.9/43.6; S1 71.4/51.3/52.4/67.0/6.0/28.6/54.2; S2 73.3/64.6/54.3/68.6/6.0/39.9/60.1; Maco-RL-3.8 74.5/55.2/72.3/79.0/12.0/54.2/67.0. G=8, 256 traj/update. No public GitHub as of 2026-11-27 (`code_status: none`).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.34703`
- Code: `none found (`code_status: none`).`
