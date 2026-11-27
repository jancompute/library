---
id: paper:tune-for-retention
type: paper
title: 'Tune for Retention: SFT Forgets Less at Lower LR and Batch'
authors:
- Nirmit Joshi
- Nathan Srebro
- Eran Malach
year: 2026
month: 11
arxiv_id: '2611.34579'
url: https://arxiv.org/abs/2611.34579
methods:
- method:olmo-3
- method:aclarena
cites:
- paper:olmo-3
- paper:instructreplay
- paper:sycophancy-from-sft
tags:
- sft
- forgetting
- retention
- gotcha
---

# Tune for Retention: SFT Forgets Less at Lower LR and Batch

## Abstract Summary
Instruction SFT forgets pretrain / prior-skill behavior as a function of learning rate and batch size more than of the mix. Lower LR and smaller batches retain more of the source checkpoint at matched new-task gain. Distinct from InstructReplay (assistant-turn replay) and from ACLArena's specialist LoRA experts. Does not retarget OLMo-3 Dolci.

## Key Contributions
1. Retention is an HP surface, not only a data-mix surface.
2. Lower LR / smaller batch improves source-task retention at matched target gain.
3. Code nirmitj6/tune-for-retention-sft.

## Empirical Highlights
SFT runs that look equal on the new task can differ sharply on source-task holdout once LR and batch move. Replay / mix interventions are not a substitute for this HP axis. Does not retarget OLMo-3 or ACLArena.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.34579`
- Code: `https://github.com/nirmitj6/tune-for-retention-sft`
