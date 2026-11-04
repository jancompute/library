---
id: paper:toolspace
type: paper
title: 'ToolSpace: Tool-Centric Environments from MCP Traces'
authors:
- 'Guanting Dong'
- 'Yutao Zhu'
- 'Chenghao Zhang'
- 'Jiaheng Liu'
- 'Hongjin Qian'
- 'Zhicheng Dou'
year: 2026
month: 11
arxiv_id: '2611.05036'
url: https://arxiv.org/abs/2611.05036
methods:
- method:toolspace
cites:
- paper:codemidas
- paper:synthapi
tags:
- environments
- tool-use
- active
---

# ToolSpace: Tool-Centric Environments from MCP Traces

## Abstract Summary
ToolSpace synthesizes tool-centric RL environments from real MCP traces rather than from repository source. Qwen3.6-35B-A3B 23.0→41.0 (43.2 after RL); GLM-5.2 44.6→56.6.

## Key Contributions
1. Tool-centric env factory from MCP traces.
2. SFT then RL lifts on Qwen3.6-35B-A3B and GLM-5.2.

## Empirical Highlights
Qwen3.6-35B-A3B 23.0→41.0 (43.2 RL); GLM-5.2 44.6→56.6.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.05036`
- Code: `https://github.com/dongguanting/ToolSpace` (`code_status: released`).
