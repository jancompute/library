---
id: method:dram
type: method
title: DRAM
category: optimizer
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'full-param FT optimizer-state memory (ternary column-wise one-sparse)'
    reason: 'TACO is ternary one-sparse FT; DRAM is principal-random subspace Muon'
    use_instead: method:taco
  - when: 'choosing the memory-efficient full-parameter first hop'
    reason: 'SCALE remains subspace-projection SOTA; DRAM is principal-random rank reallocation, no SCALE bake-off'
    use_instead: method:scale
  - when: 'native FP4 forward/backward hardware training from scratch'
    reason: 'Quartet-II is native FP4 training; DRAM is BF16 Muon subspace memory'
    use_instead: method:quartet-ii
  - when: 'quality LoRA on 24GB without a fully quantized checkpoint constraint'
    reason: 'Quality default remains vanilla LoRA + rsLoRA + LR sweep'
    use_instead: method:lr-matters-lora
  - when: 'mixed-precision scaling law for which pass to keep high precision (not optimizer-state memory)'
    reason: 'DRAM does not choose which pass to keep high precision'
    use_instead: method:mixed-precision-scaling
  - when: 'structure-aware Muon on Monarch-factored weights (not SCALE subspace)'
    reason: 'Monarch-Muon is structured-weight Muon; DRAM is subspace rank reallocation'
    use_instead: method:monarch-muon
  - when: 'subspace Muon with residual correction (PMRC / SMRC)'
    reason: 'PMRC is residual-correction subspace; DRAM is principal-random rank reallocation'
    use_instead: method:pmrc
  - when: 'choosing the ~7B dense pretrain optimizer'
    reason: 'Muon2 remains the ~7B optimizer default; DRAM is a memory-efficient Muon plug-in'
    use_instead: method:muon2
assumptions:
  - 'LLaMA 60M/130M/350M C4 pretrain; Qwen3-8B, LLaMA-3.1-8B, Gemma-2-9B full-parameter FT. Rank k=8 (60M) / 16 (130M) / 32 (350M/FT). Linear (r,q) from (k-1,1) to (0,k). Peak mem vs Full-Muon 17.9–20.7%. No public code as of 2026-11-24. No SCALE bake-off.'
last_reviewed: '2026-11-24'
papers:
- paper:dram
recipes:
- recipe:dram
claims:
- benchmark: 'LLaMA 60M/130M/350M C4 pretrain, low-memory Avg (ARC/HellaSwag/OBQA/PIQA)'
  metric: 'Avg accuracy'
  value: '36.28 / 37.19 / 38.55 vs GaLore-Muon 35.94 / 36.82 / 37.93 vs Full-Muon 36.47 / 37.32 / 40.21'
  baseline: 'GaLore-Muon; Full-Muon; APOLLO; Fira; PAdam'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.28595'
  notes: 'Best low-memory at all three scales. Full-Muon still leads 350M. Does not retarget SCALE or Muon2.'
- benchmark: 'Qwen3-8B / LLaMA-3.1-8B / Gemma-2-9B full-parameter FT, peak GPU mem vs Full-Muon'
  metric: 'peak GiB; relative cut'
  value: 'Qwen3-8B 52.80→42.47 (19.6%); LLaMA-3.1-8B 50.81→40.31 (20.7%); Gemma-2-9B 60.25→48.06 (20.2%); 17.9–20.7% across 9 FT settings'
  baseline: 'Full-Muon; GaLore-Muon; APOLLO; Fira; PAdam'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.28595'
  notes: 'Best low-memory in 8/9 FT settings; matches/exceeds Full-Muon in 8/9. Qwen3-8B IF/math/code 50.46/84.16/72.20 vs Full-Muon 50.46/84.16/71.60. No public GitHub.'
tags:
- optimizer
- muon
- memory-efficient
- subspace
- active
---

# DRAM

## Method Overview
DRAM runs Muon momentum and matrix-sign normalization inside a compact principal-random subspace. The basis mixes TopSVD principal directions with random directions from the orthogonal complement. Rank starts principal-heavy at \((k-1,1)\) and reallocates linearly toward random coverage \((0,k)\). Stochastic \(O(T^{-1/4})\) and deterministic \(O(T^{-1/2})\) rates hold for nondecreasing coverage schedules.

## When to Use
- Full-parameter Muon when peak GPU memory is the constraint and a principal-random subspace plus rank reallocation is acceptable.

## When NOT to Use
The ~7B optimizer remains `method:muon2`. SCALE remains the memory-efficient full-param first hop. Residual-correction subspace remains `method:pmrc`. Ternary FT remains `method:taco`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:full-param-memory-efficient-pretrain`. Mention on `task:llm-pretraining-optimization`. Distinct from SCALE, PMRC, GaLore-Muon, Monarch-Muon. Does **not** replace SCALE or Muon2.

## Gotchas & Failure Modes
- No public code at ingest (`code_status: none`).
- Full-Muon still leads 350M C4 Avg (40.21 vs 38.55); DRAM is the low-memory win, not an unconstrained Muon replacement.
- No SCALE bake-off; do not cite DRAM as beating SCALE.
