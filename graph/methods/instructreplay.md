---
id: method:instructreplay
type: method
title: InstructReplay
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'general chat / instruct SFT without L2 language fidelity'
    reason: 'OLMo-3 remains the open instruct stack; InstructReplay is assistant-turn replay during factual FT'
    use_instead: method:olmo-3
  - when: 'instruct FT under a behavioral-drift budget / layer-selective freeze of instruct models rather than LoRA composition'
    reason: 'DCO chooses update direction under an anchored-KL budget; InstructReplay matches frozen M0 on saved assistant turns'
    use_instead: method:dco
  - when: 'SFT-free RL-only domain adaptation from a base model (OnePO / HuatuoGPT-3)'
    reason: 'OnePO is RL-only domain adaptation; InstructReplay is factual FT plus replay'
    use_instead: method:onepo
assumptions:
  - 'Instruction-tuned starting checkpoint. 9600 general instructions answered once by frozen M0; mix domain NLL with full next-token match on those assistant turns. Three families × two domains. Code xiaofengShi/InstructReplay as of 2026-11-25.'
last_reviewed: '2026-11-25'
papers:
- paper:instructreplay
recipes:
- recipe:instructreplay
claims:
- benchmark: 'three families × two domains, five general benches vs standard factual FT'
  metric: 'average general-bench decline; domain accuracy'
  value: 'decline 28.1→2.4; matches standard FT on new facts. Standard FT −35 points and halves answer length (SmolLM3-3B IFEval 71%→9%)'
  baseline: 'standard factual FT; seven adaptation methods'
  date: '2026-11-25'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.32918'
  notes: 'Gain is from replaying M0 answers to general instructions, not from the loss form. BOS-token or domain-answer replay fails. Code xiaofengShi/InstructReplay.'
tags:
- sft
- replay
- instruct
- active
---

# InstructReplay

## Method Overview
The initial instruction-tuned model answers a fixed set of general instructions once. During factual fine-tuning the student is kept close to those frozen assistant-turn distributions while learning the new facts. Standard FT collapses answer length and tanks IFEval / reasoning / code.

## When to Use
- Closed-book factual FT of an already-instructed checkpoint when general assistant behavior must stay intact.

## When NOT to Use
Open instruct SFT remains `method:olmo-3`. Drift-budget layer-selective FT remains `method:dco`. RL-only domain adaptation remains `method:onepo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:instruct-sft-alignment`. Distinct from DCO, OnePO, AutoSFT, ACLArena. Does **not** replace OLMo-3 or DCO.

## Gotchas & Failure Modes
- Replay must use the chat template and the model's own assistant turns; BOS-token or domain-answer replay does not protect general benches.
- Matching sampled tokens instead of full next-token distributions is weaker.
- MMLU option-likelihood barely moves; the damage is in generated-answer benches.
