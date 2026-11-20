---
id: paper:diffusion-rl-is-steering
type: paper
title: 'RL Post-Training in Diffusion Transformers Is Activation Steering'
authors:
- Tuna Han Salih Meral
- Kaan Oktay
- Alec Helbling
- Atakan Kara
- Duen Horng Chau
- Pinar Yanardag
year: 2026
month: 11
arxiv_id: '2611.26627'
url: https://arxiv.org/abs/2611.26627
methods:
- method:diffusion-opsd
cites: []
tags:
- diffusion
- rl
- steering
- claim-note
---

# RL Post-Training in Diffusion Transformers Is Activation Steering

## Abstract Summary
Claim note on `method:diffusion-opsd` / `task:posttrain-diffusion`, not a trainer. Constant per-block steering vectors (0.29M params vs 18.8M rank-32 LoRA on SD3.5-M) fitted to match RL-tuned velocity, with no reward in the objective, recover 90.0–96.3% of the reward gain of six RL-tuned image models (89.8% and 111.9% on two video models). Does not retarget DiffusionOPSD or Self-OPD.

## Key Contributions
1. Most measured diffusion-RL reward gain is an input-independent activation shift.
2. Image tokens reading steered text keys/values carry the gain (resetting that path keeps 20.5% / 10.5% of OCR / PickScore).
3. Same-size LoRA shows no detected advantage over the steering vectors.

## Empirical Highlights
SD3.5-M / FLUX.1-dev: 90.0–96.3% of six image RL reward gains. Wan2.1 / Wan2.2-5B: 89.8% and 111.9%.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.26627`
