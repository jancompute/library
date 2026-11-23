---
id: method:rollout-reuse
type: method
title: Rollout Reuse
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation (reverse-KL on student rollouts)'
    reason: 'OPD remains matching; this reuses saved teacher GRPO traces via SFT then DPO'
    use_instead: method:opd
  - when: 'privileged same-size gold teacher OPSD'
    reason: 'VISTA is gold-solution privileged OPSD, not archive reuse'
    use_instead: method:vista
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; this is student distillation from a finished teacher archive'
    use_instead: method:cispo
assumptions:
  - 'Teacher GRPO traces, rewards, and per-token logp were saved. No extra teacher generation. Teacher-top1 uses cached teacher likelihoods, not a student scoring pass (GRAPE). Students include Gemma-2-2B, LFM2.5-1.2B, Qwen2.5-1.5B, SmolLM3-3B, Qwen3-4B. Code vashistht/rollout_reuse as of 2026-11-23.'
last_reviewed: '2026-11-23'
papers:
- paper:rollout-reuse
recipes:
- recipe:rollout-reuse
claims:
- benchmark: 'Maths avg@8 across two teachers, five students, five benches vs canonical teacher regen'
  metric: 'avg@8 gap vs D_synthetic'
  value: '-0.37 (95% CI [-0.82, +0.08]); naive SFT -1.95 [-2.33, -1.58]'
  baseline: 'Canonical distillation (new teacher generation on Math12K); naive random-rollout SFT'
  date: '2026-11-23'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.26803'
  notes: 'Avoids 58.3M maths + 17.6M coding regen tokens. Coding naive SFT is 4.44 below canonical. Gemma-2-2B MATH500 4.3%→17.1% with SFT warm start. Does not retarget method:opd.'
tags:
- distillation
- opd
- grpo
- sft
- dpo
- active
---

# Rollout Reuse

## Method Overview
Keep the teacher's GRPO archive. Order prompts by pass rate. SFT the student on teacher-top1 correct completions (cached teacher logp as a student-compatibility proxy), then DPO on mixed-success prompts. No extra teacher generation and no student scoring pass.

## When to Use
- A finished teacher RL run already stored traces, rewards, and logp, and you want students without regenerating a synthetic set.

## When NOT to Use
Reverse-KL matching on the student's own rollouts remains `method:opd`. Gold-solution privileged OPSD remains `method:vista`. Training the teacher with Pass@1 RLVR remains `method:cispo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Distinct from OPD (token KL on student states). GRAPE (student-top1 scoring) is a paper baseline, not a library node.

## Gotchas & Failure Modes
- Naive SFT on the archive underperforms canonical distillation; the two-stage recipe is the method.
- Standalone DPO collapses on low-support students (Gemma-2-2B, LFM2.5-1.2B); the SFT warm start is required there.
- Teacher-top1 is student-agnostic; GRAPE can win when you can afford a student scoring pass.
