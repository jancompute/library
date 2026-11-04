---
id: paper:you-dont-need-long-context
type: paper
title: "You Don't Need Long Context"
authors:
- 'Peter Belcak'
- 'Saurav Muralidharan'
- 'Jindong Jiang'
- 'Yonggan Fu'
- 'Wonmin Byeon'
- 'Hanrong Ye'
- 'Ryan Angilly'
- 'Ali Taghibakhshi'
- 'Shih-Yang Liu'
- 'Siru Ouyang'
- 'Greg Heinrich'
- 'Pavlo Molchanov'
year: 2026
month: 11
arxiv_id: '2611.05306'
url: https://arxiv.org/abs/2611.05306
methods:
- method:rlm
- method:memento
cites:
- paper:rlm
- paper:memento
tags:
- long-context
- gotcha
---

# You Don't Need Long Context

## Abstract Summary
Compaction can replace a long native window for many dumped-document jobs. This is a no-train inference note on task:long-context-prompt-offload, not a new offload trainer.

## Key Contributions
1. Compaction-without-retrain as a long-context alternative to native windows / RLM.

## Empirical Highlights
Gotcha on dumped-prompt offload. Does not retarget RLM or MEMENTO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.05306`
- Code: none found (`code_status: none`).
