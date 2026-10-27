---
id: method:dtca
type: method
title: 'DTCA'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:diffusion-lm-ar-delta-recycle'
  reason: 'A2D recycles an AR delta; DTCA is dLLM RL token credit during denoising'
  use_instead: method:a2d
- when: 'dLLM RL that forks from high-entropy intermediate states (ForkGRPO)'
  reason: 'ForkGRPO forks rollouts; DTCA reweights denoising-token credit'
  use_instead: method:forkgrpo
assumptions:
- 'dLLM RL credit assignment. No public code as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:dtca
recipes:
- recipe:dtca
claims:
- benchmark: 'LLaDA-8B-Instruct MATH500 / GSM8K vs unweighted dLLM RL'
  metric: 'accuracy vs base'
  value: 'up to +9.0 MATH500 and +5.3 GSM8K over the base model across generation budgets'
  baseline: 'base LLaDA-8B-Instruct; unweighted dLLM RL'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.35201'
  notes: 'Does not retarget method:a2d or method:forkgrpo.'
tags:
- diffusion
- rlvr
- active
---

# DTCA

## Method Overview
DTCA scores a committed token by the confidence lift it gives remaining masked positions, groups those scores by POS, picks informative denoising steps, and rescales by entropy change after the update.

## When to Use
- Discrete diffusion RL where outcome reward cannot tell which unmask step mattered.

## When NOT to Use
Default on `task:diffusion-lm-ar-delta-recycle` remains `method:a2d`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:a2d`.

## Gotchas & Failure Modes
- Not a replacement for `method:a2d`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
