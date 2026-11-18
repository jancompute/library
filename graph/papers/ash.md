---
id: paper:ash
type: paper
title: Get Hint-Augmented GRPO Done Right Through Activation Steering
authors:
- Khiem Le
- Ting Hua
- Nitesh V. Chawla
year: 2026
month: 11
arxiv_id: '2611.23124'
url: https://arxiv.org/abs/2611.23124
methods:
- method:ash
cites: []
tags:
- rlvr
- hints
- activation-steering
- grpo
- active
---

# Get Hint-Augmented GRPO Done Right Through Activation Steering

## Abstract Summary
Hint-Augmented GRPO (HA-GRPO) appends a hint at train time that is missing at inference. ASH (Activation Steering for Hinting) trains a residual steering vector on hinted vs plain rollouts so inference injects the hint-conditioned behavior without a hint in context. Qwen3-4B-Base pass@8 math avg 50.54 GRPO → 55.83 ASH, OOD 66.86 → 70.47; vs HILL 53.58 / 68.34. Four backbones (Qwen3-1.7B/4B-Base, Llama-3.2-1B/3B-Instruct). No public GitHub (verl). Distinct from H2R, Guided-RLVR, SV-Training, ASE. Does not retarget CISPO.

## Key Contributions
1. Reinterprets hinting as a question-agnostic behavioral shift, not a difficulty reduction.
2. Joint hinted/plain rollouts plus a trainable residual steering vector that is injected at inference.
3. ~1.5× GRPO train time vs ~2× for SAGE/HILL, with consistent pass@8 gains on six benches.

## Empirical Highlights
Qwen3-4B-Base pass@8 math avg 50.54 → 55.83; OOD 66.86 → 70.47 vs HILL 53.58 / 68.34. Qwen3-1.7B-Base / Llama-3.2-1B/3B-Instruct also gain on AMC, OlympiadBench, AIME24/25, Minerva, GPQA-Diamond.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.23124`
- Code: `none found` (`code_status: none`; paper uses verl).
