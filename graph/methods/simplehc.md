---
id: method:simplehc
type: method
title: SimpleHC
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'choosing the frontier MoE architecture template'
    reason: 'DeepSeek-V4 / Kimi-K3 remain the MoE co-default; SimpleHC is a cheaper Hyper-Connection layout, not a template swap'
    use_instead: method:deepseek-v4
  - when: 'manifold-constrained Hyper-Connections as used in DeepSeek-V4 (mHC)'
    reason: 'mHC remains the Sinkhorn hyper-connection in V4; SimpleHC drops residual mixing for a smaller train-time tax'
    use_instead: method:mhc
  - when: 'multi-stream attention residuals vs vanilla / mHC / AttnRes (MSAR)'
    reason: 'MSAR is a residual-topology bake-off; SimpleHC is a Hyper-Connection simplification'
    use_instead: method:msar
assumptions:
  - 'Hyper-Connection residual streams (HC / mHC) where residual mixing and per-stream memory dominate train time. Paper: 15B/30B MoE. GitHub aHapBean/SimpleHC is README+PDF as of 2026-11-13.'
last_reviewed: '2026-11-13'
papers:
- paper:simplehc
recipes:
- recipe:simplehc
claims:
- benchmark: '15B/30B MoE loss and avg; train-time overhead vs vanilla at C=6144; backward storage'
  metric: 'loss; avg score; extra train time; backward storage vs mHC'
  value: 'loss 1.561, avg 63.1 vs mHC 62.9; extra train time 2.4% vs vanilla (mHC ~7.0%); backward storage −31%'
  baseline: 'mHC / vanilla residual'
  date: '2026-11-13'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.05984'
  notes: 'Does not retarget method:mhc or method:deepseek-v4. Mention on task:pretrain-moe-frontier. Hugging Face Daily leftover (2611.05984, below watermark).'
tags:
- architecture
- hyper-connections
- mhc
- pretraining
- active
---

# SimpleHC

## Method Overview
SimpleHC is a Hyper-Connection layout that drops residual mixing and shares memory access. Learned read/write gating stays. On 15B/30B MoE it matches mHC loss and average score while cutting the train-time tax versus vanilla (2.4% vs mHC ~7.0% at C=6144) and reducing backward storage by 31%.

## When to Use
- HC / mHC residual streams where mixing and per-stream memory dominate, and a cheaper layout is wanted without changing the DeepSeek-V4 template.

## When NOT to Use
Frontier MoE architecture remains `method:deepseek-v4` / `method:kimi-k3`. Manifold-constrained HC in V4 remains `method:mhc`. Multi-stream attention residuals remain `method:msar`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:llm-pretraining-optimization`. Mention on `task:pretrain-moe-frontier`. Does **not** replace mHC or DeepSeek-V4.

## Gotchas & Failure Modes
- GitHub `aHapBean/SimpleHC` is README plus paper PDF as of 2026-11-13 (`code_status: announced`).
- Matching mHC at 15B/30B is not a V4 architecture bake-off.
- Do not confuse with MSAR residual topology.
