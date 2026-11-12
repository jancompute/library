---
id: task:agent-memory
type: task
title: "Agent Memory"
domain: "agents"
summary: "Persistent agent context: incremental playbooks, not rewrite, not recursive summary as long-context."
scope: "How an agent stores and updates strategies across tasks. Not dumped-prompt RLM and not a SWE loop."
out_of_scope:
  - "Recursive summary as the only long-context strategy"
  - "SWE patch loops with no playbook need"
  - "Dumped 10M-token prompt"
  - "System-One control plane for conversational memory ops (Jev-Mem)"
redirects:
  - when: "evidence-linked memory / WikiTrace (not write-time playbook)"
    to: "method:wikitrace"
  - when: "file-based coding-agent memory via async OPD (CAMP-II; not write-time playbook)"
    to: "method:camp-ii"
  - when: "evolving ontology relational memory + RL reasoning-state (EvoMemState; not write-time playbook)"
    to: "method:evomemstate"
  - when: "multi-view OPSD of skill memory (MDSkill; not write-time playbook)"
    to: "method:mdskill"
  - when: "memory tax / net value of agent memory vs naive RAG"
    to: "paper:memory-tax"
  - when: "lessons that carry chance from noisy outcomes into the next decision"
    to: "paper:luck-carrying-lessons"
  - when: "unified online RL of construction and retrieval for agent memory (Uni-Mem)"
    to: "method:uni-mem"
  - when: "dumped corpus ≫ window"
    to: "task:long-context-prompt-offload"
  - when: "SWE issue-to-patch without a playbook"
    to: "task:software-engineering-agent-harness"
  - when: "repository-grounded procedural skills before interaction experience"
    to: "method:code2skill"
  - when: "System-One control plane for memory ops (typing, routing, budget, traversal)"
    to: "method:jev-mem"
  - when: "read-time curation of raw trajectories (not write-time playbook)"
    to: "method:jitmem"
  - when: "recurrent textual harness that backward-revises retrieved reflections (not write-time playbook)"
    to: "method:reharness"
last_reviewed: '2026-11-12'
current_sota:
  - method: method:ace
    as_of: "2025-10"
    benchmark: "AppWorld, DeepSeek-V3.1"
    metric: "success %"
    value: "ACE 59.4 vs ReAct 42.4 (+17); vs GEPA latency −82%"
    notes: "Incremental bullets. Without feedback ACE/DC can degrade. Dynamic Cheatsheet collapse 18282 tok @66.7 → 122 tok @57.1."
methods:
  - method:wikitrace
  - method:camp-ii
  - method:evomemstate
  - method:mdskill
  - method:uni-mem
  - method:reharness
  - method:ace
  - method:memgpt
  - method:code2skill
  - method:jev-mem
  - method:jitmem
tags:
  - agents
  - agent-memory
  - ace
  - memgpt
---

# Agent Memory

## Problem Definition
Agents need memory that accumulates strategies without collapsing under rewrite. Recursive summary is not this task (and fails as long-context).

## Evaluation Protocol & Benchmarks
- AppWorld (ACE vs ReAct / GEPA).
- DMR for MemGPT. Sleep-time compute as a persona-agent complement.

## SOTA Landscape
- **Active (evidence-linked memory, not this playbook default)**: `method:wikitrace` (`arXiv:2611.14320`). Insight → compilation → raw trajectory; descend with terminal tools. $90.2$ vs No Memory $79.5$; Regression $6.5\%\to 4.5\%$. Code yukyeongleee/wikitrace. Complements `paper:luck-carrying-lessons` / `paper:memory-tax`. Does not replace ACE.
- **Active (file-based coding-agent memory via OPD, not this playbook default)**: `method:camp-ii` (`arXiv:2611.14009`). CAMG-II $64.6$ vs CAMP-I $54.2$; TB 2.1 Qwen3.5-4B $23.1\to 30.0$. No public code. Mentions on `task:agent-continual-learning` / `task:student-distillation`. Does not replace ACE.
- **Active (relational + RL reasoning-state, not this playbook default)**: `method:evomemstate` (`arXiv:2611.03743`). MemSyco Qwen3-8B $57.6\%$ ($+12.2$); Acc@complete LoCoMo-Refined / MemSyco $70.8\%$ / $68.5\%$. Code XMUDeepLIT/EvoMemState. Does not replace ACE.
- **Active (multi-view skill OPSD, not this playbook default)**: `method:mdskill` (`arXiv:2611.05313`). ALFWorld/WebShop up to +7.1/+8.1. Code announced anonymous.4open.science/r/MDSKILL-CF53. Does not replace ACE.
- **current_sota**: ACE (`method:ace`).
- **Active**: MemGPT for long-lived persona agents.
- **Active (repository-grounded skills)**: `method:code2skill` (`arXiv:2609.05571`) — lift code units into verified skill records before interaction experience. ACE remains the playbook/memory default.
- **Active (System-One-controlled store)**: `method:jev-mem` (`arXiv:2609.23986`) — typed control plane for typing, routing, budget, traversal, scoring, stop; System Two only for hard reasoning. LoCoMo judge 0.777. Does not replace ACE or Code2Skill.
- **Active (read-time curator)**: `method:jitmem` (`arXiv:2609.27334`) — keep raw trajectories; curate at read time from immediate task success. ALFWorld/WebShop/τ² +16.2/+16.3/+3.9 vs write-time baselines. Does not retarget ACE.
- **Active (recurrent reflection harness, not this playbook default)**: `method:reharness` (`arXiv:2610.12668`) on `task:agent-continual-learning`. Edits retrieved reflections after the instance. Does not replace ACE, Code2Skill, or Jev-Mem.
- **Gotcha (memory tax)**: `paper:memory-tax` (`arXiv:2610.34073`). Eleven memory systems vs naive RAG; many underperform two-round RAG. Keep a raw-history retrieval path. Complements paper:luck-carrying-lessons. Does not retarget ACE.
- **do_not_use**: recursive summary as the only long-context strategy.
