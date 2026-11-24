---
id: task:elastic-depth-looped-lm
type: task
title: Elastic-Depth Looped Language Models
domain: pretraining
summary: Train one looped LM whose decode-time loop count can vary, using mixed loop
  counts during optimization rather than a single fixed recurrence depth.
scope: Elastic / mixed-depth looped LM training (gated state update, mixed loop counts
  per optimizer step, loop-index/budget conditioning, late mixed-depth conversion).
  First hop is ELR. Not Huginn-style fixed-point looping, not compute-matched MoE
  layer looping, not CED all-token recurrence.
out_of_scope:
- Huginn-style dense fixed-point looped LMs (Looped Models Done Right)
- Compute-matched MoE looping of middle layers (SMELT)
- Recurrent CED all-token recurrence (RLT)
- Standard dense ~7B NTP optimizer (Muon2)
redirects:
- when: convert the student to cross-token recurrence during OPD (Recurrent Student OPD; not mixed-depth ELR / not Concertina)
  to: method:recurrent-student-opd
- when: residual looped pretrain / Loopback Transformer (not mixed-depth ELR)
  to: method:loopback-transformer
- when: fold N teacher layers into a shared loop then FKL+CE (Concertina; not mixed-depth ELR)
  to: method:concertina
- when: nGPT looped 4B with difficulty-aware loop curriculum (Dory; not ELR default)
  to: method:dory
- when: train all depths as a candidate set (Best-of-Depth; not ELR default)
  to: method:best-of-depth
- when: FLOP-matched dense looped pretrain via progressive depth copy (UpLoop)
  to: method:uploop
- when: post-train loops on a finished checkpoint (no-free-loop)
  to: paper:no-free-loop
- when: Huginn-style dense fixed-point looped LMs (learned depth prior / terminal
    KV sharing)
  to: method:looped-models-done-right
- when: compute-matched MoE looping of middle layers (FLOPs/params/KV matched)
  to: task:compute-matched-moe-looped-pretrain
- when: experimental CED all-token recurrence, not mixed-depth looping
  to: task:recurrent-encoder-decoder-lm
- when: standard dense ~7B NTP from scratch
  to: task:pretrain-dense-7b
- when: nested width-elastic supernet rather than mixed-depth looping
  to: method:shell-elastic
current_sota:
- method: method:elr
  as_of: '2026-10-13'
  benchmark: 4B dense / 30B-A3B MoE 10-task avg vs matched unlooped baseline
  metric: score delta at 1 loop / 4 loops
  value: 4B −0.52 / +7.25; 30B-A3B +1.04 / +4.75
  notes: ELR (2610.12582). Method status active. Listed here as first hop; method
    sota_for stays empty. Does not replace Looped Models Done Right or SMELT.
methods:
- method:recurrent-student-opd
- method:loopback-transformer
- method:concertina
- method:dory
- method:best-of-depth
- method:uploop
- method:shell-elastic
- method:elr
- method:looped-models-done-right
- method:smelt
- method:recurrent-looped-transformer
last_reviewed: '2026-11-24'
tags:
- pretraining
- looped-lm
- elr
- elastic-depth
---

# Elastic-Depth Looped Language Models

## Problem Definition
A looped LM is usually trained at one recurrence depth. This task owns **one weight set that is trained under mixed loop counts** so decode can pick 1–K loops, including a late conversion of an unlooped checkpoint.

This is **not** Huginn-style fixed-point looping and not SMELT's compute-matched MoE layer looping.

## Evaluation Protocol
- **Primary Benchmarks**: 10-task avg vs a matched unlooped baseline at 1 loop and at 4 loops (paper: 4B dense, 30B-A3B MoE); optional AAII (Koi-4B).
- **Evaluation Pitfalls**: Do not cite SMELT FLOP-savings or Huginn KV-sharing as ELR results. One-loop 4B dense can sit slightly below the unlooped baseline.

## SOTA Recommendation (as of 2026-10-13)
- **Related recurrent student OPD (not this first hop)**: `method:recurrent-student-opd` (`arXiv:2611.28603`) on `task:student-distillation`. Cross-token recurrence during OPD, not mixed-depth looping. No public code. Does not replace ELR.
- **Related residual looped pretrain (not this first hop)**: `method:loopback-transformer` (`arXiv:2611.07226`) on `task:llm-pretraining-optimization`. Stores residual updates; matched tokens and executed depth. Code yancyou/Loopback. Does not replace ELR.
- **Related teacher-layer folding (not this first hop)**: `method:concertina` (`arXiv:2611.18113`) on `task:student-distillation`. Folds an existing teacher, not mixed-depth from scratch. Code myboker/concertina. Does not replace ELR.
- **Optional nGPT looped 4B recipe (not this first hop)**: `method:dory` (`arXiv:2611.03998`). 6T tokens (4.5T NVFP4); 12-bench 35.2→39.7→40.6 at k=1/2/4. Weights on Hugging Face; official train code none. Does not replace ELR.
- **Optional all-depth candidate set (not this first hop)**: `method:best-of-depth` (`arXiv:2611.04663`). N-Queens coverage 91.03% vs 45.75% final-depth. No public code. Does not replace ELR.
- **Primary (this task only)**: **ELR** (`method:elr`, `paper:elr` `arXiv:2610.12582`). Status `active`. Listed here as first hop; method `sota_for` stays empty. No public code.
- **Not This Task**: `method:looped-models-done-right` remains Huginn-style dense looping; `method:smelt` remains compute-matched MoE looping; `method:recurrent-looped-transformer` remains experimental CED.
- **Not this task (nested width, not mixed depth)**: `method:shell-elastic` (`arXiv:2610.15124`) on `task:llm-pretraining-optimization`. Does not replace ELR.
- **Optional FLOP-matched dense upcycling**: `method:uploop` (`arXiv:2610.41720`). 1.3B 22-task avg 22.99→27.52. No public code. Does not replace ELR.
- **Gotcha (post-train loops)**: `paper:no-free-loop` (`arXiv:2610.42030`). Loops added after pretrain pay only at 0.8B; 4B/9B fail the equal-parameter test. Does not retarget ELR.
