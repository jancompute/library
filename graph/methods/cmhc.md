---
id: method:cmhc
type: method
title: cmHC
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'choosing the ~7B dense pretrain optimizer'
    reason: 'cmHC is a residual-mixing geometry on mHC-lite bases, not the optimizer; Muon2 remains the 7B default'
    use_instead: method:muon2
  - when: 'Hyper-Connection simplification without residual mixing (SimpleHC; not mHC default)'
    reason: 'SimpleHC drops residual mixing; cmHC contracts mixing toward the Birkhoff interior'
    use_instead: method:simplehc
  - when: 'TP-grouped Hyper-Connections vs mHC (TPHC; not SimpleHC / not mHC default)'
    reason: 'TPHC is tensor-parallel grouped updates; cmHC is geometric contraction of permutation bases'
    use_instead: method:tphc
  - when: 'choosing the frontier MoE architecture template'
    reason: 'DeepSeek-V4 / Kimi-K3 remain the MoE pretrain co-default; cmHC is a residual plug-in'
    use_instead: method:deepseek-v4
assumptions:
  - 'Host is mHC-lite permutation-basis mixing. Default λ=0.97 on the first K=2 layers; no new parameters. nanoGPT-S/M/L on 8xH100, 10k steps. 6B-MoE at 71.5k; 300B-MoE gap is at 2k steps only. Fused kernels are Ascend 910C / CANN 9.1.0. Code Newiz430/cmHC as of 2026-11-23.'
last_reviewed: '2026-11-23'
papers:
- paper:cmhc
recipes:
- recipe:cmhc
claims:
- benchmark: 'OpenWebText nanoGPT-S/M/L val loss vs mHC-lite'
  metric: 'validation loss drop'
  value: '-0.0073 / -0.0024 / -0.0045'
  baseline: 'mHC-lite'
  date: '2026-11-23'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.27193'
  notes: 'λ=0.97, K=2. Best average loss rank vs Residual / HC / mHC / mHC-lite / KromHC. FineWeb-Edu is mixed: lowest train+val on M (K=10), competitive on S.'
- benchmark: '6B-MoE pretrain vs mHC / mHC-lite at 71.5k steps'
  metric: 'training loss gap'
  value: '-0.002 vs mHC / -0.005 vs mHC-lite'
  baseline: 'mHC; mHC-lite'
  date: '2026-11-23'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.27193'
  notes: '300B-MoE is -0.0157 vs mHC at 2k steps only (early, caveat). Ascend fused hyper-connection latency -44.8% at D=2048.'
tags:
- architecture
- hyper-connections
- pretraining
- moe
- active
---

# cmHC

## Method Overview
mHC-lite parameterizes residual mixing as a convex combination of permutation matrices. Those matrices sit near Birkhoff vertices (under-mixing). cmHC replaces each basis with a contracted doubly stochastic matrix \(\tilde{P}=\lambda P+(1-\lambda)11^{\top}/n\), default \(\lambda=0.97\) on the first \(K=2\) layers, so mixing enters the polytope interior without new parameters. Stronger or deeper contraction drives streams toward the uniform barycenter (over-mixing).

## When to Use
- Pretraining an mHC-lite (or permutation-basis) hyper-connection stack and residual matrices have collapsed to near-permutations.

## When NOT to Use
The 7B optimizer remains `method:muon2`. Dropping residual mixing remains `method:simplehc`. TP-grouped Hyper-Connections remain `method:tphc`. Frontier MoE architecture remains DeepSeek-V4 / Kimi-K3.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:llm-pretraining-optimization`. Mention on `task:pretrain-moe-frontier`. Distinct from mHC Sinkhorn, SimpleHC, and TPHC. Does **not** replace Muon2 or mHC.

## Gotchas & Failure Modes
- \(\lambda\to 1/n\) or large \(K\) over-mixes streams; keep moderate contraction on shallow layers.
- 300B-MoE evidence is a 2k-step early gap, not a finished bake-off.
- Fused kernels are Ascend-specific; GPU latency is not the headline claim.
