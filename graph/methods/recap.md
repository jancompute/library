---
id: method:recap
type: method
title: RECAP
category: agent-recursion
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'dumped corpus ≫ window'
    reason: 'RLM remains dumped-prompt offload; RECAP jointly trains compaction with a long-horizon agent policy'
    use_instead: method:rlm
  - when: 'long tool/web/SWE trajectory with folding as the first hop'
    reason: 'FoldGRPO remains folding SOTA; RECAP is a behavior-distortion objective on compact vs full-context actions'
    use_instead: method:foldgrpo
  - when: 'outcome-only long-horizon agent RL (coverage / anti-drift or rubric credit)'
    reason: 'CANOPY remains coverage RL; RECAP is compaction training, not sparse-outcome grouping'
    use_instead: method:canopy
  - when: 'trained compaction notes inside a 20K window (MEMENTO)'
    reason: 'MEMENTO trains book-QA notes; RECAP trains agent summaries that preserve post-compaction actions'
    use_instead: method:memento
assumptions:
  - 'Qwen3.5-4B, thinking off, 32K working context, up to three compaction events, k=1 recent turn kept. VeRL async GRPO, group 8, lr 1e-6, 150 steps. λ=0.1 BrowseComp-Plus / 0.03 SWE. Code eth-medical-ai-lab/recap as of 2026-11-25.'
last_reviewed: '2026-11-25'
papers:
- paper:recap
recipes:
- recipe:recap
claims:
- benchmark: 'Qwen3.5-4B 32K compaction vs GRPO, BrowseComp-Plus / SWE-bench Verified'
  metric: 'accuracy'
  value: 'BrowseComp-Plus 62.8 vs GRPO 58.2 (+4.6); SWE-bench Verified 51.1 vs GRPO 46.8 (+4.3)'
  baseline: 'task-reward GRPO with the same compaction'
  date: '2026-11-25'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.31258'
  notes: '128K GRPO without compaction 63.8 / 55.5. Distortion gradient splits into summary reward plus post-compaction self-distill. Code eth-medical-ai-lab/recap.'
tags:
- agents
- compaction
- grpo
- active
---

# RECAP

## Method Overview
RECAP jointly trains a long-horizon agent policy and its context summaries so a compact history induces the same subsequent actions as the original history. Behavior distortion KL between compact-conditioned and full-context action distributions splits into a summary reward and a post-compaction self-distillation term on a GRPO host.

## When to Use
- Training an agent that must compact tool/search/SWE history inside a fixed working window, and task-reward GRPO alone leaves post-compaction drift.

## When NOT to Use
Dumped-corpus offload remains `method:rlm`. Trajectory folding as the first hop remains `method:foldgrpo`. Sparse-outcome coverage remains `method:canopy`. Book-QA notes remain `method:memento`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:long-horizon-tool-agent`. Mentions on `task:long-context-prompt-offload` and `task:outcome-only-long-horizon-agent-rl`. Distinct from FoldGRPO, RLM, MEMENTO, TACM, Mosaic. Does **not** replace FoldGRPO, RLM, or CANOPY.

## Gotchas & Failure Modes
- Summary-reward \(g_{\mathrm{sum}}\) alone can lengthen summaries and drop BrowseComp-Plus; keep the post-compaction self-distill term.
- \(\lambda\) is environment-specific (0.1 vs 0.03); tune on a held-out set.
- SWE-bench Verified 51.1 is a 4B compaction transfer, not a harness ranking vs mini-SWE-agent.
