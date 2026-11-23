---
id: paper:gumbel-substitution
type: paper
title: 'Gumbel Substitution: Removing Sampler Drift from RL Without Trusting the Sampler'
authors:
- Romain Fanucci
- Malik El Hassani
year: 2026
month: 11
arxiv_id: '2611.27375'
url: https://arxiv.org/abs/2611.27375
methods:
- method:gumbel-substitution
cites: []
tags:
- rl
- sampler-drift
- gumbel
- importance-sampling
---

# Gumbel Substitution: Removing Sampler Drift from RL Without Trusting the Sampler

## Abstract Summary
Untrusted samplers inject SFT-toward-\(q\) drift. TIS/MIS/IcePop/CISPO need \(q(y)\). Gumbel substitution draws public \(G\); the sampler returns \(y=\arg\max(\ell^q+G)\) and the trainer scores \(v^*=\arg\max(\ell^p+G)\). For a protocol-following sampler, \(v^*\) is an exact sample from \(p\). Distinct from TRACE / TRIAGE / DLC.

## Key Contributions
1. Public-Gumbel token substitution that removes sampler drift without trusting \(q(y)\).
2. Lab bound: uncorrected drift 170–4800× substitution; 2B mismatch collapse vs substitution.
3. Permissionless 9B Reliquary production run with 1.21% substituted tokens.

## Empirical Highlights
9B, 158 steps, 15.75B tokens, match 0.979. SWE-bench Verified 17.3→43.6; TMax 28.4→74.8; LiveCodeBench +21.3; AIME 2025 73.3→91.2. Not a TRACE bake-off.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.27375`
- Code: `https://github.com/reliquadotai/reliquary`
