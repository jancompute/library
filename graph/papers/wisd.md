---
id: paper:wisd
type: paper
title: 'Weaken to Strengthen: Weakening-Induced On-Policy Self-Distillation for Large Reasoning Models'
authors:
- 'Yecheng Wu'
- 'Song Han'
- 'Han Cai'
year: 2026
month: 10
arxiv_id: '2610.38681'
url: https://arxiv.org/abs/2610.38681
methods:
- method:wisd
cites:
- paper:opsa
tags:
- opsd
- teacher-free
- active
---

# Weaken to Strengthen: Weakening-Induced On-Policy Self-Distillation for Large Reasoning Models

## Abstract Summary
WISD builds a weaker copy of the model by low-bit quantization or magnitude pruning and uses the contrast with the original as an on-policy self-distillation signal, with no privileged information.

## Key Contributions
1. Teacher-free weakening-induced OPSD via quant or prune.

## Empirical Highlights
Quant +4.0pp / prune +5.5pp avg. Qwen3.5-4B HMMT 2025 57.7→70.5 and LiveCodeBench v6 39.1→56.7 (prune). Qwen3.6-35B-A3B 68.5→74.6 / 61.8→69.5 (quant). Code jet-ai-projects/WISD. Does not retarget method:opsa.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.38681`
- Code: `https://github.com/jet-ai-projects/WISD (`code_status: released`).`
