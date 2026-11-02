---
id: paper:byod
type: paper
title: 'BYOD: Build Your Own DLM - Efficient Autoregressive-to-Diffusion Language Model Conversion'
authors:
- 'Ruurd J. A. Kuiper'
- 'Robert A. Bagheri'
year: 2026
month: 10
arxiv_id: '2610.41574'
url: https://arxiv.org/abs/2610.41574
methods:
- method:byod
cites:
- paper:a2d
- paper:justopd
tags:
- dllm
- lora
- active
---

# BYOD: Build Your Own DLM

## Abstract Summary
BYOD is a LoRA-only AR-to-masked-DLM conversion. Base weights stay frozen; adapters are 4.1-5.8% of final parameters. Converts Gemma 2 9B, Llama 3.1 8B, Qwen2.5 7B, and Ministral 8B in 3.1-4.0 hours on one Colab GPU with at most 102.4M tokens. BYOD-Gemma averages 50.6% vs LLaDA 8B Instruct 51.9% on nine tasks. Open-generation perplexity at low NFE remains the gap: 8.3-11.1 vs LLaDA 4.1 and AR parents 2.2-3.0 at 128 tokens / 64 steps.

## Key Contributions
1. LoRA-only AR to masked DLM conversion without architecture-specific full FT.

## Empirical Highlights
Code github.com/RuurdKuiper/BYOD. Distinct from method:a2d (weight-delta recycle) and method:justopd (on-policy distill).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.41574`
- Code: `https://github.com/RuurdKuiper/BYOD` (`code_status: released`).
