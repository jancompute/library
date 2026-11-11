---
id: method:camp-ii
type: method
title: 'CAMP-II (Coding Agent Memory Post-Training II)'
category: agent-memory
status: active
sota_for: []
supersedes: []
do_not_use_for:
    - when: 'write-time playbook memory (ACE default)'
      reason: 'ACE remains the agent-memory first hop; CAMP-II trains file-as-memory via asynchronous OPD'
      use_instead: method:ace
    - when: 'multi-stage agent capability stacking / continual learning'
      reason: 'ACLArena remains the CL first hop; CAMP-II is memory-protocol OPD, not LoRA experts'
      use_instead: method:aclarena
    - when: 'trained self-call + range-read harness (TACM)'
      reason: 'TACM is an 8K context-management harness; CAMP-II uses ordinary Bash files as memory'
      use_instead: method:tacm
assumptions:
    - 'Ordinary Bash + episode-persistent workspace as the memory interface (shared teacher/student prior). Fully asynchronous OPD from a frozen teacher. No public GitHub as of 2026-11-11. Paper: Qwen3.5-4B/9B, CAMG-II + Terminal-Bench 2.1 / SWE-Bench Pro V2. arXiv 2611.14009 above watermark 2611.12886.'
last_reviewed: '2026-11-11'
papers:
- paper:camp-ii
recipes:
- recipe:camp-ii
claims:
- benchmark: 'CAMG-II five-domain mean / Terminal-Bench 2.1 / SWE-Bench Pro V2'
  metric: 'success vs CAMP-I / initial student'
  value: 'CAMG-II 64.6 vs CAMP-I 54.2 (2.97× strongest OPD-baseline gain); TB 2.1 23.1→30.0 (4B) / 38.0 (9B); SWE-Bench Pro V2 11.2→18.1 / 23.1→30.1'
  baseline: 'CAMP-I / dedicated-memory-tool OPD / initial Qwen3.5-4B/9B'
  date: '2026-11-11'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.14009'
  notes: 'Does not retarget method:ace or method:aclarena. CAMP-I is not a library node. CAMP-II-9B beats Qwen3.5-35B-A3B on TB 2.1 (38.0 vs 33.8) and SWE-Bench Pro V2 (30.1 vs 27.4).'
tags:
- agent-memory
- opd
- files
- continual-learning
- active
---

# CAMP-II (Coding Agent Memory Post-Training II)

## Method Overview
CAMP-II trains one policy across five long-horizon CAMG-II environments with fully asynchronous OPD. Memory is ordinary files in an episode-persistent workspace, not a dedicated memory tool. The frozen teacher already has a file-operation prior, so it can score what the student writes. Dedicated memory tools starve both sides: the teacher has never used the interface, and the student samples too few valid memory actions.

## When to Use
- Long-horizon agents that must survive context replacement, and both teacher and student already speak Bash/files.

## When NOT to Use
Write-time playbook remains `method:ace`. Agent continual learning remains `method:aclarena`. Trained 8K compaction harness remains `method:tacm`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:agent-memory`. Mentions on `task:agent-continual-learning` and `task:student-distillation`. Does **not** replace ACE or ACLArena.

## Gotchas & Failure Modes
- No public GitHub (`code_status: none`).
- CAMP-I is not a library node; do not add a supersedes edge.
- Masking the OPD loss on memory-write tokens removes most of the gain; the skill is what to write, not the task actions.
- Pair with `paper:memory-tax`: many memory systems lose to naive RAG.
