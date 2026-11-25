---
id: task:long-horizon-tool-agent
type: task
title: "Long-Horizon Tool Agent"
domain: "agents"
summary: "Long trajectory of tools/web/SWE with a small active context. Different from dumped-prompt RLM."
scope: "Many sequential tool steps whose history must be folded. Not dumped-prompt offload and not the SWE harness without folding."
out_of_scope:
  - "Dumped corpus prompt offload (RLM)"
  - "SWE harness without folding"
  - "Async RL training without a folding objective (SAO)"
  - "Outcome-only long-horizon agent RL (CANOPY / DRACO)"
  - "Live-web multi-hop search-agent training without a folding objective (Iris)"
  - "Structural tool vs summary credit under GRPO (SLCA-GRPO)"
redirects:
  - when: "behavior-distortion compaction RL (RECAP; not FoldGRPO folding / not RLM)"
    to: "method:recap"
  - when: "dumped corpus much larger than the window"
    to: "task:long-context-prompt-offload"
  - when: "SWE harness without folding"
    to: "task:software-engineering-agent-harness"
  - when: "outcome-only long-horizon agent RL (signal starvation / drift or outcome-blind rubrics)"
    to: "task:outcome-only-long-horizon-agent-rl"
  - when: "train a live-web multi-hop search agent (SFT-RL climbing), not folding"
    to: "task:web-search-agent-rl"
  - when: "structural credit split for tool-call vs natural-language-summary tokens (not folding)"
    to: "task:tool-agent-segment-credit"
last_reviewed: "2026-11-25"
current_sota:
  - method: method:foldgrpo
    as_of: "2025-10"
    benchmark: "BrowseComp-Plus / SWE-Bench Verified, Seed-OSS-36B 32K×10"
    metric: "score"
    value: "BrowseComp-Plus 0.620 vs ReAct 327K+GRPO 0.540 vs ReAct 32K 0.286; SWE-Bench Verified 0.580 vs ReAct 327K+GRPO 0.574; GPT-5 ReAct 0.793 / 0.718 still ahead"
    notes: "36B-class SOTA, not frontier-model SOTA."
methods:
  - method:recap
  - method:foldgrpo
  - method:agentfold
  - method:rao
  - method:pta
  - method:iris
  - method:slca-grpo
tags:
  - agents
  - agent-recursion
  - foldgrpo
  - long-horizon
---

# Long-Horizon Tool Agent

## Problem Definition
The agent takes many tool/web/SWE steps. The problem is the **trajectory**, not a dumped prompt. Keep a small active context by folding completed sub-trajectories.

## Evaluation Protocol & Benchmarks
- BrowseComp-Plus, SWE-Bench Verified at 32K×10 vs ReAct 32K and ReAct 327K+GRPO.
- Record GPT-5 ReAct as still ahead.

## SOTA Landscape
- **Optional behavior-distortion compaction RL (not this folding default)**: `method:recap` (`arXiv:2611.31258`). Qwen3.5-4B 32K BrowseComp-Plus 62.8 vs GRPO 58.2 (+4.6); SWE-Verified 51.1 vs 46.8 (+4.3). Code eth-medical-ai-lab/recap. Mentions on `task:long-context-prompt-offload` / `task:outcome-only-long-horizon-agent-rl`. Distinct from RLM / MEMENTO / TACM / Mosaic. Does not replace FoldGRPO, RLM, or CANOPY.
- **current_sota**: FoldGRPO (`method:foldgrpo`). Unchanged.
- **Active**: AgentFold (web history, 36.2% BrowseComp); RAO (trained recursion, TextCraft 24% vs 95%).
- **Related pre-RL tool OPKD (not this folding default)**: `method:pta` (`arXiv:2609.04773`) teacher-commits tool turns before Search-R1 / DeepEyes RL. Does not replace FoldGRPO.
- **Not this folding default**: live-web search-agent climbing is `task:web-search-agent-rl` (`method:iris`).
- **Not this folding default (structural tool/summary credit)**: `method:slca-grpo` on `task:tool-agent-segment-credit`. Does not replace FoldGRPO.
