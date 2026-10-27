---
id: paper:lora-task-format
type: paper
title: 'Task Format as a Factor in Adaptation: A Controlled Comparison of LoRA and Full Fine-Tuning for Prompt-Safety Classification'
authors:
- 'John Alderete'
- 'Srirakshith Betageri'
- 'Jennifer Flynn'
- 'Alex Greenhalgh'
- 'Josh Rubin'
- 'Yoshita Varma Annam'
year: 2026
month: 10
arxiv_id: '2610.33813'
url: https://arxiv.org/abs/2610.33813
methods:
- method:lr-matters-lora
cites:
- paper:lr-matters-lora
tags:
- peft
- gotcha
- lora
---

# Task Format as a Factor in Adaptation: A Controlled Comparison of LoRA and Full Fine-Tuning for Prompt-Safety Classification

## Abstract Summary
LoRA vs full FT comparisons are often confounded, and task format is rarely ablated. On prompt-safety classification with a matched 400M encoder-decoder pair, the regime matters less than learning rate and training target. Writing a reason after the verdict adds 4.0 pp for LoRA; a content-free sentence of equal length does not.

## Key Contributions
1. Task-format / LR confound for LoRA vs full FT; not a quality-LoRA replacement.

## Empirical Highlights
At pre-specified LRs full FT leads LoRA by 2-3 pp; the encoder gap closes under a shared LR search. In-domain accuracy is an incomplete robustness guide (jailbreaks -8 to -23 pp vs a prompted 8B).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.33813`
- Code: `none found (`code_status: none`).`
