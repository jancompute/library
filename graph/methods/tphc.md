---
id: method:tphc
type: method
title: TPHC
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'grouped Hyper-Connection residual read/write (GHC; not cmHC / not SimpleHC / not TPHC)'
    reason: 'TPHC groups streams for tensor-parallel updates; GHC groups computation inside a residual branch'
    use_instead: method:ghc
  - when: 'contract mHC permutation bases toward the Birkhoff barycenter (cmHC; not SimpleHC / not mHC default)'
    reason: 'TPHC groups streams for tensor-parallel updates; cmHC contracts permutation bases toward the Birkhoff interior'
    use_instead: method:cmhc
  - when: 'choosing the frontier MoE architecture template'
    reason: 'DeepSeek-V4 / Kimi-K3 remain the MoE co-default; TPHC is a TP-grouped Hyper-Connection layout, not a template swap'
    use_instead: method:deepseek-v4
  - when: 'manifold-constrained Hyper-Connections as used in DeepSeek-V4 (mHC)'
    reason: 'mHC remains the Sinkhorn hyper-connection in V4; TPHC groups streams for tensor-parallel updates'
    use_instead: method:mhc
  - when: 'Hyper-Connection simplification without residual mixing (SimpleHC)'
    reason: 'SimpleHC drops residual mixing; TPHC keeps grouped TP updates'
    use_instead: method:simplehc
  - when: 'multi-stream attention residuals vs vanilla / mHC / AttnRes (MSAR)'
    reason: 'MSAR is a residual-topology bake-off; TPHC is a Hyper-Connection TP grouping'
    use_instead: method:msar
assumptions:
  - 'Hyper-Connection residual streams (HC / mHC) under tensor parallelism. Paper: 1.1B / 100B SlimPajama; 8B TP-sharded TPHC4. Code wuyou2002/TPHC released as of 2026-11-18.'
last_reviewed: '2026-11-23'
papers:
- paper:ghc
- paper:cmhc
- paper:tphc
recipes:
- recipe:tphc
claims:
- benchmark: '1.1B / 100B SlimPajama val loss and avg; 8B TP-sharded train time'
  metric: 'val loss; avg score; train-time vs mHC4'
  value: 'TPHC4 2.0838 / 48.9 vs mHC4 2.0985 / 48.6; TPHC8 2.0706 / 49.3 vs mHC8 2.0924 / 48.8 and vs mHC16 2.0885 / 49.0; 8B TP-sharded TPHC4 +9% train time vs mHC4'
  baseline: 'mHC4 / mHC8 / mHC16'
  date: '2026-11-18'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.23026'
  notes: 'Does not retarget method:mhc, method:simplehc, or method:deepseek-v4. Mention on task:pretrain-moe-frontier. Code wuyou2002/TPHC.'
tags:
- architecture
- hyper-connections
- mhc
- tensor-parallel
- pretraining
- active
---

# TPHC

## Method Overview
TPHC groups Hyper-Connection residual streams so tensor-parallel ranks update local groups instead of replicating the full mix. Sparse per-group writes keep stream diversity. Sharded streams keep N=4→16 expansion cheaper than replicated mHC.

## When to Use
- HC / mHC residual streams under tensor parallelism where replicated mixing dominates train time.

## When NOT to Use
Frontier MoE architecture remains `method:deepseek-v4` / `method:kimi-k3`. Manifold-constrained HC in V4 remains `method:mhc`. Drop-mixing simplification remains `method:simplehc`. Multi-stream attention residuals remain `method:msar`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:llm-pretraining-optimization`. Mention on `task:pretrain-moe-frontier`. Does **not** replace mHC, SimpleHC, or DeepSeek-V4.

## Gotchas & Failure Modes
- TPHC8 beating mHC16 at 1.1B is not a V4 architecture bake-off.
- Do not confuse with SimpleHC (drops residual mixing) or MSAR (attention residuals).
