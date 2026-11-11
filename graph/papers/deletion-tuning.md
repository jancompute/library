---
id: paper:deletion-tuning
type: paper
title: 'The Surprising Effectiveness of Deleting Weights in LLM Post-Training'
authors:
- Jack Lu
- Zhenbang Yang
- Mike Lasby
- Tejas Pote
- Yani Ioannou
- Mengye Ren
year: 2026
month: 11
arxiv_id: '2611.10866'
url: https://arxiv.org/abs/2611.10866
methods:
- method:deletion-tuning
cites: []
tags:
- peft
- sparsity
- deletion
- continual-learning
- active
---

# The Surprising Effectiveness of Deleting Weights in LLM Post-Training

## Abstract Summary
Deletion Tuning zeros fewer than $0.05\%$ of pretrained weights, with no other modification, and matches full fine-tuning across GRPO, SFT, and on-policy distillation. Llama-3-8B GSM8K $83.55$ vs FFT $83.24$. Prior-task accuracy stays near the base while FFT/LoRA/MTH lose up to $5.4$ points. Hugging Face Daily leftover 2026-11-10. Code agentic-learning-ai-lab/deleting-weights released.

## Key Contributions
1. Binary mask over gate projections is the entire adapter.
2. Matches FFT at the largest backbone in each family (Llama 8B, Qwen 7B / 14B / 30B-A3B).
3. Compact (8.4 MB at Llama8B) and low forgetting (forward KL $\le 0.05$).

## Empirical Highlights
Llama8B GSM8K $83.55$ vs FFT $83.24$; Qwen7B SimpleRL-Zoo $52.32$ vs $51.89$. Does not retarget lr-matters-lora.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.10866`
- Code: `https://github.com/agentic-learning-ai-lab/deleting-weights` (`code_status: released`).
- Project: `https://agenticlearning.ai/deleting-weights/`
