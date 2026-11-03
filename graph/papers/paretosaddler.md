---
id: paper:paretosaddler
type: paper
title: 'ParetoSaddler: Pareto-Guided Optimization of Agent Harnesses for Quality and Cost'
authors:
- 'Xingzhi Qian'
- 'Sungho Park'
- 'Rongyuan Tan'
- 'Jianbo Yu'
- 'Jue Zhang'
- 'Lorenzo Cavallaro'
- 'Menglin Xia'
- 'Yanzhi Chen'
- 'Xinnuo Xu'
- 'Yu Kang'
- 'Xinran Zheng'
- 'Gagan Somashekar'
- 'Xuchao Zhang'
- 'Chetan Bansal'
- 'Qingwei Lin'
- 'Victor Rühle'
year: 2026
month: 11
arxiv_id: '2611.02079'
url: https://arxiv.org/abs/2611.02079
methods:
- method:paretosaddler
cites:
- paper:activesaddler
tags:
- harness
- pareto
- active
---

# ParetoSaddler: Pareto-Guided Optimization of Agent Harnesses for Quality and Cost

## Abstract Summary
Quality-only harness search rejects intermediate candidates that later help cost. ParetoSaddler separates promotion from deployment: Bayesian bootstrap Pareto support promotes parents that improve quality or cost, then a deployment preference picks the final harness. Sibling of ActiveSaddler (failure-pattern curriculum).

## Key Contributions
1. Pareto quality+cost harness search with delayed deployment preference.

## Empirical Highlights
ClawMark 70.86% to 81.35% and $1.17 to $1.01; GAIA2 56.22% to 62.89% and $0.78 to $0.45. Beats quality-only harness optimization on both axes.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.02079`
- Code announced: `https://aka.ms/ParetoSaddler-website` (`code_status: announced`).
