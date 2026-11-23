---
id: method:gumbel-substitution
type: method
title: Gumbel Substitution
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'FP4 RL train-side vs rollout-side quantization mismatch (TRACE / TRIAGE)'
    reason: 'TRACE/TRIAGE align NVFP4 train–rollout numerics with trusted engines; this removes sampler drift without q(y)'
    use_instead: method:trace
  - when: 'discrepancy-lag correction of sampler/trainer mismatch (DLC)'
    reason: 'DLC splits numerical discrepancy from policy lag on trusted logp; this substitutes tokens via public Gumbel'
    use_instead: method:dlc
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; substitution is a drift correction when q is untrusted'
    use_instead: method:cispo
  - when: 'variable environment latency / async stragglers, not untrusted-sampler drift'
    reason: 'SAO remains async straggler RL; this is permissionless-sampler drift'
    use_instead: method:sao
assumptions:
  - 'Coordinator broadcasts public Gumbel G per token, bit-identical across GPUs. Sampler implements y=argmax(ℓ^q+G). Trainer scores v*=argmax(ℓ^p+G) in the sampler prefix. Production Reliquary numbers are one 9B RL run that uses substitution, not a TRACE bake-off. Code reliquadotai/reliquary as of 2026-11-23.'
last_reviewed: '2026-11-23'
papers:
- paper:gumbel-substitution
recipes:
- recipe:gumbel-substitution
claims:
- benchmark: 'Lab 9B matched-head uncorrected drift vs substitution; 2B mismatch collapse'
  metric: 'expected drift ratio; training stability'
  value: 'uncorrected drift 170–4800× substitution; 2B uncorrected collapses, substitution ≈ MIS+score-centering with true q'
  baseline: 'uncorrected on-policy scoring of sampler tokens; MIS + score centering with true q'
  date: '2026-11-23'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.27375'
  notes: 'Does not need q(y). Distinct from TRACE/TRIAGE/DLC.'
- benchmark: 'Reliquary 9B permissionless RL, 158 steps, 15.75B tokens, 161 sampler accounts, 7 envs'
  metric: 'SWE-bench Verified pass@1; TMax; match rate; substituted fraction'
  value: 'SWE-bench Verified 17.3→43.6 (×2.5); TMax 28.4→74.8 (×2.6); LiveCodeBench +21.3; AIME 2025 73.3→91.2; match 0.979; 1.21% substituted; no skipped/clipped step'
  baseline: 'same 9B run before RL (not TRACE)'
  date: '2026-11-23'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.27375'
  notes: 'Table 12 n=486 SWE-bench (7 need network, 7 gold patches fail sandbox). Production numbers are an RL run USING substitution, not a TRACE bake-off. Do not overclaim vs TRACE/TRIAGE.'
tags:
- rl
- sampler-drift
- gumbel
- distributed-rl
- active
---

# Gumbel Substitution

## Method Overview
Untrusted samplers produce \(q\neq p\). Scoring \(y\sim q\) adds SFT-toward-\(q\) drift, and IS corrections need \(q(y)\). The coordinator samples public Gumbel noise \(G\) once per token. The sampler returns \(y=\arg\max(\ell^q+G)\). The trainer substitutes \(v^*=\arg\max(\ell^p+G)\) and scores \(v^*\) in the sampler's prefix. Protocol-following samplers yield exact samples from \(p\), so the drift vanishes without trusting reported probabilities. Match rate \(1[y=v^*]\) also admits and pays samplers.

## When to Use
- Permissionless or heterogeneous rollout workers where \(q(y)\) cannot be trusted, and you control the sampling protocol (Gumbel-argmax).

## When NOT to Use
Trusted-engine FP4 train–rollout mismatch remains TRACE / TRIAGE. Trusted-logp lag remains `method:dlc`. Pass@1 RLVR remains `method:cispo`. Async stragglers remain `method:sao`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:fp4-rl-train-rollout-alignment`. Mention on `task:agentic-async-rl`. Distinct from TRACE / TRIAGE / DLC / CIS-RL / CISPO. Does **not** replace TRACE / TRIAGE.

## Gotchas & Failure Modes
- Production SWE-bench / AIME numbers are one Reliquary RL run that uses substitution, not a bake-off against TRACE.
- Adaptive samplers that ignore G still inject drift; admission is the match-rate gate, not a cryptographic guarantee.
- Table 12: 7 of 486 SWE-bench items need network; 7 gold patches fail the sandbox.
