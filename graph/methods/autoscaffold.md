---
id: method:autoscaffold
type: method
title: AutoScaffold
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; AutoScaffold is a frozen-teacher training-time scaffold on a GRPO/GiGPO host'
    use_instead: method:cispo
  - when: 'adaptive ground-truth rationale scaffolding for sparse-reward RLVR (RGPO / GA-GRPO)'
    reason: 'RGPO is GT-rationale scaffolding; AutoScaffold writes class/instance scaffolds from the training log'
    use_instead: method:rgpo
  - when: 'hierarchical hint-based reward for math RLVR (H2R)'
    reason: 'H2R scores sub-question milestones; AutoScaffold injects prompt scaffolds and removes them at eval'
    use_instead: method:h2r
  - when: 'outcome-only long-horizon agent RL (coverage / anti-drift or rubric credit)'
    reason: 'CANOPY remains AppWorld coverage; AutoScaffold is a scaffold overlay, not a coverage kernel'
    use_instead: method:canopy
  - when: 'train a live-web multi-hop search agent (SFT-RL climbing)'
    reason: 'Iris remains the search-agent first hop; AutoScaffold is a GiGPO scaffold overlay on synthetic search QA'
    use_instead: method:iris
assumptions:
  - 'Frozen teacher with query tools over the student training log. Host is GRPO, DAPO, or GiGPO. Scaffolds are prompt-only and removed at eval. No public trainer as of 2026-11-12. arXiv 2611.14515 is the 2026-11-12 listing high ingest.'
last_reviewed: '2026-11-12'
papers:
- paper:autoscaffold
recipes:
- recipe:autoscaffold
claims:
- benchmark: 'ALFWorld GiGPO / search QA / math GRPO-DAPO / KernelBench, scaffold-free eval'
  metric: 'pp vs corresponding RL baseline'
  value: 'ALFWorld +7.2 success; search QA +4.0 EM; math up to +2.0 avg; KernelBench correctness +3.0 / faster-than-PyTorch +5.0; QuestA match at ~1/3 student steps'
  baseline: 'GiGPO / GRPO / DAPO / QuestA / human-designed scaffolds'
  date: '2026-11-12'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.14515'
  notes: 'Does not retarget method:cispo, method:canopy, or method:iris. Validation ablation -14.1 ALFWorld. Sibling of method:rgpo / method:h2r / method:eps-prompt-scaffolding.'
tags:
- rlvr
- scaffolding
- grpo
- active
---

# AutoScaffold

## Method Overview
AutoScaffold is a frozen-teacher overlay on group-relative RLVR. Every $K$ steps the teacher inspects the student's training experience, writes class-level strategies and instance-level hints, validates class-level edits on held-out tasks, and injects the kept scaffolds into training prompts with $q[C]\le q_{\max}<1$. Rollouts are scored by the original task reward. Scaffold tokens receive no gradient. Evaluation is scaffold-free.

## When to Use
- GRPO/DAPO/GiGPO hosts where all-fail groups starve the update and you can afford a frozen teacher that reads the training log.

## When NOT to Use
Pass@1 remains `method:cispo`. GT-rationale scaffolding remains `method:rgpo`. Hierarchical hint rewards remain `method:h2r`. AppWorld coverage remains `method:canopy`. Live-web search climbing remains `method:iris`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:math-code-rl-dense`. Mentions on `task:outcome-only-long-horizon-agent-rl` and `task:web-search-agent-rl`. Does **not** replace CISPO, CANOPY, or Iris.

## Gotchas & Failure Modes
- Over-strong scaffolds make every rollout succeed and zero the group advantage.
- Needs a teacher that can query trajectories and validate class-level edits; dropping validation cost $14.1$ ALFWorld points in the paper.
- No public trainer as of 2026-11-12.
