---
id: method:itdm
type: method
title: iTDM
category: diffusion-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'aligning text-to-image diffusion or flow models with rewards as the first hop'
    reason: 'DiffusionOPSD remains on-policy self-distill; iTDM is instantaneous trajectory distribution matching that restores baseline invariance under CFG / off-policy rollouts'
    use_instead: method:diffusion-opsd
  - when: 'teacher-free flow matching multi-objective alignment (Self-OPD)'
    reason: 'Self-OPD remains teacher-free flow matching; iTDM is a forward-RL velocity match with an auxiliary denoiser'
    use_instead: method:self-opd
  - when: 'flow-model RL via proximal velocity matching (~100 updates vs Flow-GRPO ~4k)'
    reason: 'MEND is proximal velocity matching; iTDM is the infinitesimal TDM limit with a sample-level gradient anchored at the behavior velocity'
    use_instead: method:mend
  - when: 'aggregation-first reward tilting for diffusion RL (~12× fewer GPU-hrs vs DiffusionNFT / Flow-GRPO-Fast)'
    reason: 'DiffusionART tilts rewards by aggregation; iTDM fixes signed-RWR baseline drift'
    use_instead: method:diffusionart
assumptions:
  - 'Forward diffusion RL with deterministic ODE rollouts. Auxiliary denoiser tracks the behavior velocity. Online and offline / CFG-mismatched rollouts. SD3.5-M and FLUX.3 5.6B. Code Luo-Yihong/iTDM as of 2026-11-25. HF Daily leftover below listing watermark.'
last_reviewed: '2026-11-25'
papers:
- paper:itdm
recipes:
- recipe:itdm
claims:
- benchmark: 'GenEval2 vs competing forward diffusion RL'
  metric: 'convergence; score'
  value: '~3× faster; scales smoothly to 0.87 without collapse'
  baseline: 'signed RWR / existing forward diffusion RL'
  date: '2026-11-25'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.30986'
  notes: 'Behavior–policy mismatch under CFG / off-policy breaks baseline invariance of signed RWR. Auxiliary denoiser restores exact baseline invariance at its optimum. Code Luo-Yihong/iTDM. HF Daily leftover (2611.30986).'
- benchmark: 'FLUX.3 5.6B HPSv3++ guidance-free (CFG=1.0)'
  metric: 'in-domain and unseen preference metrics'
  value: 'scales to 5.6B FLUX.3 with better in-domain and unseen scores than competing forward RL'
  baseline: 'competing forward diffusion RL'
  date: '2026-11-25'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.30986'
  notes: 'Does not retarget DiffusionOPSD or Self-OPD.'
tags:
- diffusion
- rl
- flow-matching
- active
---

# iTDM

## Method Overview
Existing forward diffusion RL is signed reward-weighted regression of the policy velocity onto behavior rollouts. That assumes \(v_\theta=v_q\), which fails under CFG, off-policy updates, and imperfect online self-consistency, so baseline subtraction injects drift. iTDM takes the infinitesimal Trajectory Distribution Matching limit, yielding a sample-level gradient anchored at the behavior velocity via the posterior-score identity, and tracks that velocity with an online auxiliary denoiser.

## When to Use
- Forward / ODE diffusion RL where CFG or off-policy rollouts make signed RWR collapse or stagnate.

## When NOT to Use
Reward OPSD remains `method:diffusion-opsd`. Teacher-free flow matching remains `method:self-opd`. Proximal velocity matching remains `method:mend`. Aggregation-first tilting remains `method:diffusionart`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:posttrain-diffusion`. Distinct from DiffusionOPSD, Self-OPD, MEND, DiffusionART, FewStepRL, Shadow Posterior Matching. Does **not** replace DiffusionOPSD or Self-OPD.

## Gotchas & Failure Modes
- Auxiliary denoiser must stay near its optimum or baseline invariance is lost.
- Signed RWR without the behavior-velocity anchor fits few-step ODE artifacts and hurts OOD texture.
- HF Daily leftover (`2611.30986`) below the prior listing watermark; ingested as a 2026-11-25 leftover.
