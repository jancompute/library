---
id: method:levenshtein-edit-dlm
type: method
title: Levenshtein Editing (DLM)
category: diffusion
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'recycle an AR post-training weight delta onto a converted dLLM'
    reason: 'A2D remains AR-delta recycle; this is insert/delete post-train on a dLLM'
    use_instead: method:a2d
  - when: 'masked dLLM lookahead-edit SFT (LED; not AR-delta recycle)'
    reason: 'method:led is lookahead-edit SFT (2610.23122); this card is Levenshtein insert/delete (2611.23750)'
    use_instead: method:led
  - when: 'GRPO unmask/retain/remask policy on a frozen dLLM (ReMaRL)'
    reason: 'ReMaRL remasks on a frozen denoiser; Levenshtein Editing inserts and deletes'
    use_instead: method:remar
  - when: 'dLLM RL that forks from high-entropy intermediate states (ForkGRPO)'
    reason: 'ForkGRPO is GRPO-family RL; this is insert/delete post-train'
    use_instead: method:forkgrpo
  - when: 'curriculum RL for a discrete diffusion LM (canvas anneal)'
    reason: 'CanvasAnneal is canvas RL; this is Levenshtein editing'
    use_instead: method:canvasanneal
assumptions:
  - 'Masked diffusion LM. Insert/delete plus remask. Paper: LLaDA2.1-Mini 16B. MUST NOT use slug led (that is lookahead-edit SFT). Code inclusionAI/LLaDA2.X as of 2026-11-19.'
last_reviewed: '2026-11-19'
papers:
- paper:levenshtein-edit-dlm
recipes:
- recipe:levenshtein-edit-dlm
claims:
- benchmark: 'LLaDA2.1-Mini 16B conf-guided / conf-free / block-128'
  metric: 'paper eval avg'
  value: 'conf-guided 54.86→57.10; conf-free 27.52→47.19; block 128 36.97→51.34'
  baseline: 'LLaDA2.1-Mini 16B without Levenshtein editing'
  date: '2026-11-19'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.23750'
  notes: 'Distinct from method:led. Does not retarget method:a2d. Code inclusionAI/LLaDA2.X.'
tags:
- dllm
- levenshtein
- insert-delete
- post-training
- active
---

# Levenshtein Editing (DLM)

## Method Overview
Levenshtein Editing post-trains a masked diffusion LM with insert and delete operations in addition to remask. The paper title is LED; the library slug is `levenshtein-edit-dlm` because `method:led` is already lookahead-edit SFT.

## When to Use
- Post-train a masked dLLM when remask-only decoding underuses insert/delete.

## When NOT to Use
AR-delta recycle remains `method:a2d`. Lookahead-edit SFT remains `method:led`. Frozen remask GRPO remains `method:remar`. Entropy-fork RL remains `method:forkgrpo`. Canvas RL remains `method:canvasanneal`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:diffusion-lm-ar-delta-recycle`. Does **not** replace A2D.

## Gotchas & Failure Modes
- Do not collide with `method:led`.
- Code is on inclusionAI/LLaDA2.X (LLaDA2.2 release), not a dedicated LED repo.
