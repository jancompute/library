---
id: method:ash
type: method
title: ASH
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; ASH is hint-augmented GRPO via residual activation steering'
    use_instead: method:cispo
  - when: 'hierarchical hint-based reward for math RLVR (H2R)'
    reason: 'H2R scores sub-questions; ASH trains a residual steering vector so hints are not needed at inference'
    use_instead: method:h2r
  - when: 'steering-token exploration for RLVR (Guided-RLVR)'
    reason: 'Guided-RLVR inserts steering tokens; ASH injects a trained residual vector'
    use_instead: method:guided-rlvr
  - when: 'steering-vector residual-stream hook in SFT/distill (SV-Training)'
    reason: 'SV-Training is SFT/distill plus all-wrong GRPO repair; ASH is HA-GRPO train–infer hint matching'
    use_instead: method:sv-training
  - when: 'activation-space steering exploration for RLVR (ASE)'
    reason: 'ASE is exploration steering; ASH is hint-conditioned GRPO without a hint at inference'
    use_instead: method:ase
assumptions:
  - 'HA-GRPO host with a train-time hint that is missing at inference. Paper: Qwen3-1.7B/4B-Base and Llama-3.2-1B/3B-Instruct on verl. Distinct slug from method:ase. No public GitHub as of 2026-11-18.'
last_reviewed: '2026-11-18'
papers:
- paper:ash
recipes:
- recipe:ash
claims:
- benchmark: 'Qwen3-4B-Base pass@8 math avg / OOD (Minerva+GPQA-Diamond)'
  metric: 'pass@8'
  value: 'math avg 50.54 GRPO → 55.83 ASH; OOD 66.86 → 70.47 vs HILL 53.58 / 68.34'
  baseline: 'GRPO / HILL'
  date: '2026-11-18'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.23124'
  notes: 'Does not retarget method:cispo. Distinct from method:h2r / method:guided-rlvr / method:sv-training / method:ase. code_status none.'
tags:
- rlvr
- hints
- activation-steering
- grpo
- active
---

# ASH

## Method Overview
ASH (Activation Steering for Hinting) treats HA-GRPO hints as a question-agnostic behavioral shift. It trains a residual steering vector on hinted vs plain rollouts and injects that vector at inference so the hint is not required in context.

## When to Use
- Hint-augmented GRPO when train-time hints close the zero-reward trap but would mismatch inference context.

## When NOT to Use
Pass@1 remains `method:cispo`. Hierarchical hint rewards remain `method:h2r`. Steering tokens remain `method:guided-rlvr`. SFT/distill residual hooks remain `method:sv-training`. Exploration steering remains `method:ase`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:math-code-rl-dense`. Does **not** replace CISPO.

## Gotchas & Failure Modes
- Distinct slug from `method:ase`.
- ~1.5× GRPO train time; still cheaper than SAGE/HILL (~2×) in the paper.
- No public GitHub (`code_status: none`; verl).
