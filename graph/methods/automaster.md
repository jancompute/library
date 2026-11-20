---
id: method:automaster
type: method
title: AutoMaster
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains matching; AutoMaster is skill-guided teacher SFT'
    use_instead: method:opd
  - when: 'agentic automated SFT data research (proportion / prune / repair / replace / synthesize)'
    reason: 'AutoSFT researches mix actions; AutoMaster conditions teacher rollouts on skills'
    use_instead: method:autosft
  - when: 'distill optimized-harness behaviors into weights under a fixed target harness'
    reason: 'Harness-Zero maps harness behaviors into a fixed action space; AutoMaster is skill-conditioned SFT'
    use_instead: method:harness-zero
  - when: 'repository-grounded procedural skills before interaction experience'
    reason: 'Code2Skill lifts repo units into skills; AutoMaster uses skills to collect teacher traces'
    use_instead: method:code2skill
  - when: 'black-box NL consult then privileged OPSD+RL (COPD; not matching default)'
    reason: 'COPD is communicative OPSD+RL; AutoMaster is skill-guided SFT'
    use_instead: method:copd
assumptions:
  - 'Qwen3.5-4B/9B. 512 teacher traj, 3 epochs, lr 1e-5, batch 32. Skills in train only. Code RUCAIBox/AutoMaster as of 2026-11-20.'
last_reviewed: '2026-11-20'
papers:
- paper:automaster
recipes:
- recipe:automaster
claims:
- benchmark: 'Qwen3.5-4B/9B vs vanilla SFT (512 traj)'
  metric: 'TB2.1 / BrowseComp / Doc2Repo'
  value: '4B 22.47→28.09 / 43.24→46.13 / 32.30→33.72; 9B 26.59→35.58 / 46.85→51.53 / 36.05→40.79'
  baseline: 'vanilla SFT on the same 512 trajectories'
  date: '2026-11-20'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.26510'
  notes: '4B BrowseComp/Doc2Repo CIs include 0. Does not retarget method:opd / method:autosft / method:harness-zero / method:canopy.'
tags:
- sft
- skills
- agent
- automaster
- active
---

# AutoMaster

## Method Overview
AutoMaster (Skill-FT) prompts a teacher with a skill bank, keeps traces that use those skills, and SFT a student on the traces. The skill bank is a train-time collection harness, not part of eval.

## When to Use
- Agent SFT when a skill list can steer teacher rollouts and you would otherwise SFT on unguided traces.

## When NOT to Use
Matching distillation remains `method:opd`. SFT mix research remains `method:autosft`. Harness-to-weights remains `method:harness-zero`. Outcome-only agent RL remains `method:canopy`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Mentions on `task:instruct-sft-alignment` and `task:outcome-only-long-horizon-agent-rl`. Does **not** replace OPD, AutoSFT, or CANOPY.

## Gotchas & Failure Modes
- 4B BrowseComp and Doc2Repo intervals include zero; do not claim those as wins.
- Skills must stay out of the eval harness or the comparison is contaminated.
