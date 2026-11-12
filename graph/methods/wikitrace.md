---
id: method:wikitrace
type: method
title: WikiTrace
category: agent-memory
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'incremental playbook memory from execution feedback'
    reason: 'ACE remains the write-time playbook default; WikiTrace is evidence-linked read-time descent'
    use_instead: method:ace
  - when: 'file-based coding-agent memory via async OPD (CAMP-II; not write-time playbook)'
    reason: 'CAMP-II trains Bash-file memory with asynchronous OPD; WikiTrace is a read-time evidence store'
    use_instead: method:camp-ii
  - when: 'read-time curation of raw trajectories (not write-time playbook)'
    reason: 'JitMem curates raw traces at read time from immediate task success; WikiTrace links lessons to source runs'
    use_instead: method:jitmem
  - when: 'lessons that carry chance from noisy outcomes into the next decision'
    reason: 'Gotcha: outcome-labeled lessons can carry luck; WikiTrace is the linked-evidence mitigation, not a rewrite of that note'
    use_instead: paper:luck-carrying-lessons
  - when: 'memory tax / net value of agent memory vs naive RAG'
    reason: 'Gotcha: many memory systems lose to naive RAG; WikiTrace is a linked-lesson store, not that bake-off'
    use_instead: paper:memory-tax
assumptions:
  - 'Offline memory construction from labeled trajectories, then read-only at test. Terminal tools for descent. Code yukyeongleee/wikitrace released. Paper: five agentic benches / eight suites. arXiv 2611.14320 is a Wednesday leftover above the 11-11 ingest watermark.'
last_reviewed: '2026-11-12'
papers:
- paper:wikitrace
recipes:
- recipe:wikitrace
claims:
- benchmark: 'ALFWorld / ScienceWorld / PlanCraft / AppWorld / τ³-bench Retail, eight suites'
  metric: 'mean score vs No Memory / Insights Only; Regression'
  value: '90.2 vs No Memory 79.5 (+10.7) / Insights Only +3.2; Regression 6.5%→4.5%; best on every suite'
  baseline: 'No Memory / Insights Only / AWM / ExpeL / ReasoningBank'
  date: '2026-11-12'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.14320'
  notes: 'Does not retarget method:ace. 52% of memory-induced failures follow a memory item. Complements paper:luck-carrying-lessons / paper:memory-tax. Code yukyeongleee/wikitrace.'
tags:
- agent-memory
- active
---

# WikiTrace

## Method Overview
WikiTrace is an evidence-linked agent memory. A compiler turns each past run into a compilation (why it succeeded or failed) and at most three insights, each linked down to that compilation and the raw trajectory. At test time the agent starts from the insight pool and descends with terminal tools when an insight lacks details, conflicts with another, or came from a failed run. Insights are never rewritten after construction.

## When to Use
- Procedural memory from success/failure-labeled trajectories, when write-time lessons without source evidence cause regressions on tasks the agent already solves.

## When NOT to Use
Write-time playbook default remains `method:ace`. File-as-memory OPD remains `method:camp-ii`. Read-time raw-trace curation remains `method:jitmem`. Chance-carrying lessons remain `paper:luck-carrying-lessons`. Net-value-of-memory remains `paper:memory-tax`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:agent-memory`. Does **not** replace ACE.

## Gotchas & Failure Modes
- Memory is frozen after construction; there is no online admission or rewrite.
- Descent costs tokens; the paper sees more descent on harder tasks.
- Complements, does not replace, the memory-tax / luck-carrying notes.
