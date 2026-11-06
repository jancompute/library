---
id: method:evomemstate
type: method
title: 'EvoMemState'
category: agent-memory
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agent-memory'
  reason: 'ACE remains write-time playbook; EvoMemState is relational + RL reasoning-state memory'
  use_instead: method:ace
- when: 'unified online RL of construction and retrieval (Uni-Mem)'
  reason: 'Uni-Mem jointly trains construction and retrieval; EvoMemState trains a reasoning-state policy over ontology states'
  use_instead: method:uni-mem
- when: 'multi-view OPSD of skill memory (MDSkill)'
  reason: 'MDSkill is skill OPSD; EvoMemState is personal-agent memory state'
  use_instead: method:mdskill
- when: 'read-time curation of raw trajectories (JitMem)'
  reason: 'JitMem curates traces at read time; EvoMemState maintains relational and reasoning states'
  use_instead: method:jitmem
assumptions:
- 'Personal-agent memory with ontology facts plus RL reasoning-state. MemSyco / MemTrap / LoCoMo. Code XMUDeepLIT/EvoMemState. HF Daily 2026-11-06 leftover (2611.03743).'
last_reviewed: '2026-11-06'
papers:
- paper:evomemstate
recipes:
- recipe:evomemstate
claims:
- benchmark: 'MemSyco-Bench, Qwen3-8B / GPT-4o-mini'
  metric: 'accuracy vs strongest baseline'
  value: 'Qwen3-8B 57.6% (+12.2); GPT-4o-mini 58.9% (+5.9)'
  baseline: 'strongest compared memory system on MemSyco-Bench'
  date: '2026-11-06'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.03743'
  notes: 'Does not retarget method:ace.'
- benchmark: 'Acc@complete, Qwen3-8B'
  metric: 'accuracy on complete-retrieval questions'
  value: 'LoCoMo-Refined 70.8% (+11.5); MemSyco 68.5% (+31.2)'
  baseline: 'strongest compared memory system on the complete-evidence subset'
  date: '2026-11-06'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.03743'
  notes: 'Complete retrieval alone is not enough; the reasoning state is the use policy.'
tags:
- agents
- agent-memory
- active
---

# EvoMemState

## Method Overview
EvoMemState stores persistent facts, induces Relational States from an ontology (updates, conflicts, validity, scope), and RL-trains a policy that emits a request-specific Reasoning State (applicability, role, priority). The response model then conditions on facts plus both states.

## When to Use
- Personal / long-horizon conversational agents where retrieved facts conflict or go stale and a playbook of bullets is not enough.

## When NOT to Use
Default on `task:agent-memory` remains `method:ace`. SWE loops without a playbook remain mini-SWE-agent.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:ace`, `method:uni-mem`, `method:mdskill`, `method:jev-mem`, or `method:jitmem`.

## Gotchas & Failure Modes
- Ablations: dropping relational state hurts MemSyco more than LoCoMo; rule generation without RL does not recover the RL policy.
