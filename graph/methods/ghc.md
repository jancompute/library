---
id: method:ghc
type: method
title: Grouped Hyper-Connections (GHC)
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'choosing the ~7B dense pretrain optimizer'
    reason: 'GHC is a residual-interface architecture, not the optimizer; Muon2 remains the 7B default'
    use_instead: method:muon2
  - when: 'contract mHC permutation bases toward the Birkhoff barycenter (cmHC; not SimpleHC / not mHC default)'
    reason: 'cmHC contracts permutation bases; GHC partitions each branch into groups with distinct stream mixes'
    use_instead: method:cmhc
  - when: 'Hyper-Connection simplification without residual mixing (SimpleHC; not mHC default)'
    reason: 'SimpleHC drops residual mixing; GHC expands read/write interfaces via groups'
    use_instead: method:simplehc
  - when: 'TP-grouped Hyper-Connections vs mHC (TPHC; not SimpleHC / not mHC default)'
    reason: 'TPHC groups streams for tensor-parallel updates; GHC groups computation inside a residual branch'
    use_instead: method:tphc
  - when: 'choosing the frontier MoE architecture template'
    reason: 'DeepSeek-V4 / Kimi-K3 remain the MoE pretrain co-default; GHC is a residual plug-in'
    use_instead: method:deepseek-v4
assumptions:
  - 'Default n=4 residual streams, r=8 groups, TanhSiLU gates, freeze first-layer H_pre. 430M dense / 4BA0.2B / 13BA0.6B MoE. No public code as of 2026-11-25.'
last_reviewed: '2026-11-25'
papers:
- paper:ghc
recipes:
- recipe:ghc
claims:
- benchmark: '430M dense val loss / Avg. Score vs IHC / Pre-Norm'
  metric: 'val loss; Avg. Score'
  value: 'GHC 2.0161 / 25.80 vs IHC 2.0351 / 25.09 vs Pre-Norm 2.0713 / 23.68'
  baseline: 'IHC; Pre-Norm'
  date: '2026-11-25'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.31350'
  notes: 'Train efficiency +35% vs Pre-Norm, +10% vs IHC. n=4→8 streams GHC −0.0195 vs IHC −0.0028. No public GitHub.'
- benchmark: '13BA0.6B MoE val loss / Avg. Score vs IHC / Pre-Norm'
  metric: 'val loss; Avg. Score'
  value: 'GHC 1.6775 / 43.96 vs IHC 1.6901 / 42.59 vs Pre-Norm 1.7052 / 41.33'
  baseline: 'IHC; Pre-Norm'
  date: '2026-11-25'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.31350'
  notes: '4BA0.2B GHC 1.8862 / 31.28 vs IHC 1.9066 / 29.70. Does not retarget Muon2 or DeepSeek-V4.'
tags:
- architecture
- hyper-connections
- pretraining
- moe
- active
---

# Grouped Hyper-Connections (GHC)

## Method Overview
Hyper-Connections keep a narrow residual interface: each branch reads one stream mixture and writes scaled copies of one output. GHC partitions the branch into \(r\) groups (attention heads or FFN channels). Each group reads its own stream mix and writes a distinct output; each stream combines group outputs with learned weights. Default \(n=4\), \(r=8\), TanhSiLU, freeze first-layer \(H_{\mathrm{pre}}\).

## When to Use
- Pretraining a Hyper-Connection / IHC stack and extra streams have stopped helping because the branch still collapses to a \(c\)-dimensional read/write.

## When NOT to Use
The 7B optimizer remains `method:muon2`. Birkhoff contraction remains `method:cmhc`. Dropping residual mixing remains `method:simplehc`. TP-grouped streams remain `method:tphc`. Frontier MoE architecture remains DeepSeek-V4 / Kimi-K3.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:llm-pretraining-optimization`. Mention on `task:pretrain-moe-frontier`. Distinct from mHC, SimpleHC, TPHC, cmHC. Does **not** replace Muon2 or DeepSeek-V4.

## Gotchas & Failure Modes
- No public code at ingest (`code_status: none`).
- Freeze first-layer \(H_{\mathrm{pre}}\); signed TanhSiLU is required for group scaling.
- Extra forward memory traffic appears unless read/write mixers are fused.
