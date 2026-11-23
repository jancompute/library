---
id: method:state-kl-opd
type: method
title: State-KL OPD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains the matching default; this is a state-dependent FKL/RKL router on an OPD host'
    use_instead: method:opd
  - when: 'OPD TSD calibration (residual discrepancy during OPD, not teacher retirement)'
    reason: 'Cal-OPD gates on teacher–student discrepancy residuals; this routes on top-p coverage / underestimated mass'
    use_instead: method:cal-opd
  - when: 'OPD EOS termination gotcha / stop-id mismatch'
    reason: 'OPD-EOS is semantic-class stop ids; this is KL direction at mismatched states'
    use_instead: method:opd-eos
  - when: 'advantage-gated on-policy distillation (AOPD / when to follow the teacher)'
    reason: 'AOPD gates on advantage; State-KL routes on coverage of the teacher top-p set'
    use_instead: method:aopd
assumptions:
  - 'Qwen3-8B teacher. Students Qwen3-1.7B/4B/8B-Base. Routing p=0.9, K=16, ε1=6, ε2=0.3, ε3=0.2. Math: DAPO prompts, non-thinking teacher from Base, thinking teacher from SFT. Code: CodeR1-12k. Avg@8 / Best@8. Code zhangxinnan123/learning-dynamic-opd as of 2026-11-23.'
last_reviewed: '2026-11-23'
papers:
- paper:state-kl-opd
recipes:
- recipe:state-kl-opd
claims:
- benchmark: 'Qwen3-1.7B/4B/8B vs sampled-token OPD, Base + non-thinking Qwen3-8B teacher, math mean Avg@8 / Best@8'
  metric: 'mean Avg@8 / Best@8 points vs sampled-token OPD'
  value: '+2.36/+2.50/+1.72 Avg@8; +2.60/+4.26/+6.24 Best@8'
  baseline: 'sampled-token OPD'
  date: '2026-11-23'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.27125'
  notes: 'SFT init +2.08/+1.38/+1.59 Avg@8. Code mean Avg@8 +2.92/+3.19/+3.44; LiveCodeBench +6.00/+10.93/+8.14. Does not retarget method:opd / method:cal-opd / method:opd-eos.'
tags:
- opd
- distillation
- kl-routing
- active
---

# State-KL OPD

## Method Overview
Sampled-token reverse-KL OPD can fail at states where the student puts little mass on the teacher's top-\(p\) set, then drive sampling into regions where the teacher is unreliable. State-dependent KL routing applies forward KL when student coverage of the teacher top-\(p\) set is low or a substantial fraction of teacher mass is underestimated, otherwise reverse KL. Default: \(p=0.9\), \(K=16\), \(\varepsilon_1=6\), \(\varepsilon_2=0.3\), \(\varepsilon_3=0.2\).

## When to Use
- OPD runs that length-inflate, repeat, or show high token overlap with the teacher while accuracy drops (spurious agreement).

## When NOT to Use
Default reverse-KL matching remains `method:opd`. TSD residual gating remains `method:cal-opd`. Stop-id mismatch remains `method:opd-eos`. Advantage gating remains `method:aopd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Distinct from Cal-OPD, OPD-EOS, and AOPD. Does **not** replace OPD.

## Gotchas & Failure Modes
- Routing thresholds are paper defaults on Qwen3; retune \(p,K,\varepsilon\) if the teacher top-p set is much sharper or flatter.
- 4B SFT-init OPD variants can raise Avg@8 while cutting Best@8 (Pass@1 vs Pass@k trade-off).
- Diagnosis is on sampled-token OPD; full-vocab reverse-KL hosts are untested in the paper.
