---
id: paper:cot-proxy
type: paper
title: 'CoT-Proxy: Cross-Format Transfer for Distilling Long-Horizon Policies'
authors:
- Dawid J. Kopiczko
- Tijmen Blankevoort
- Yuki M. Asano
year: 2026
month: 11
arxiv_id: '2611.33148'
url: https://arxiv.org/abs/2611.33148
methods:
- method:cot-proxy
cites: []
tags:
- distillation
- agents
- sft
---

# CoT-Proxy: Cross-Format Transfer for Distilling Long-Horizon Policies

## Abstract Summary
A long-horizon policy can be distilled from teacher actions with an empty student reasoning block plus KL replay to the initial student. Optional CoT-proxies are short summaries after the empty block. Empty-think SFT transfers to inference with thinking on. The recipe works when the teacher hides CoT.

## Key Contributions
1. Action-only SFT with an empty think block.
2. KL replay of the student's own generations against the initial checkpoint.
3. CoT-proxies and a closed-teacher path via API reasoning summaries.

## Empirical Highlights
Qwen3-4B AppWorld 7%→18% action-only / 35% with CoT-proxy; Qwen3-32B 12%→25%. GPT-5.6 Luna closed teacher: Qwen3-4B AppWorld 7%→48%, SWE-bench Verified 3%→28%.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.33148`
- Code: none found as of 2026-11-25
