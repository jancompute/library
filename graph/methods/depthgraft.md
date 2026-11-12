---
id: method:depthgraft
type: method
title: DepthGraft
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'choosing the ~7B dense pretrain optimizer'
    reason: 'Muon2 remains the optimizer; DepthGraft is a KV-sharing architecture regularizer'
    use_instead: method:muon2
  - when: 'multi-stream attention residuals vs vanilla / mHC / AttnRes (MSAR)'
    reason: 'MSAR is residual topology; DepthGraft is hierarchical KV reconstruction'
    use_instead: method:msar
  - when: 'input-heavy agentic / KV-compressed CED serving rather than recurrent LM pretrain'
    reason: 'V4.1-Flash is serving; DepthGraft is a pretrain regularizer that also shrinks KV'
    use_instead: method:deepseek-v41-flash
  - when: 'choosing the frontier MoE architecture template'
    reason: 'DeepSeek-V4 / Kimi-K3 remain the MoE template; DepthGraft grafts KV across existing layers'
    use_instead: method:deepseek-v4
assumptions:
  - 'Pretrain from scratch or continued pretrain of dense/MoE Transformers with GQA or MLA. Paper: 0.5B–16B. Code jianke0604/DepthGraft released (same author as MSAR). HF Daily leftover below the 11-11 watermark. arXiv 2611.03142.'
last_reviewed: '2026-11-12'
papers:
- paper:depthgraft
recipes:
- recipe:depthgraft
claims:
- benchmark: '16B MoE MMLU-Pro / CMMLU / C3 vs vanilla pretrain'
  metric: 'pp vs vanilla; KV cache size'
  value: 'MMLU-Pro +7.0%; CMMLU +6.6%; C3 +6.4%; KV cache ~−1/3'
  baseline: 'vanilla dense/MoE pretrain without hierarchical KV reconstruction'
  date: '2026-11-12'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.03142'
  notes: 'Does not retarget method:muon2, method:deepseek-v4, or method:deepseek-v41-flash. Sibling of method:msar. Code jianke0604/DepthGraft.'
tags:
- pretrain
- kv-cache
- architecture
- active
---

# DepthGraft

## Method Overview
DepthGraft treats hierarchical KV sharing as a pretrain regularizer. Deep-layer keys and values are reconstructed from stride-aligned shallow–middle pairs, so the cache is a learned structural prior rather than an independent per-layer store. The same pattern applies to dense and MoE, GQA and MLA.

## When to Use
- Dense or MoE pretrain where you want a KV-sharing inductive bias and a smaller cache as a side effect, not a serving-only compression pass.

## When NOT to Use
The ~7B optimizer remains `method:muon2`. Residual topology remains `method:msar`. KV-compressed CED serving remains `method:deepseek-v41-flash`. Frontier MoE templates remain DeepSeek-V4 / Kimi-K3.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:llm-pretraining-optimization`. Mentions on `task:pretrain-dense-7b` and `task:input-heavy-agentic-moe-serving`. Does **not** replace Muon2, MSAR, or V4.1-Flash.

## Gotchas & Failure Modes
- Reconstruction is a train-time architectural constraint. Do not apply it only at decode and expect the paper's quality deltas.
- Sibling of MSAR, not a replacement: residual topology and KV reconstruction are different knobs.
