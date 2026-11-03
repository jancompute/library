---
id: paper:sftprobe
type: paper
title: 'From Weeks to Hours: Fast and Principled SFT Data Generation for Reasoning LLMs'
authors:
- 'Hongyi Henry Jin'
- 'Wenhan Yang'
- 'Meysam Ghaffari'
- 'Carlos Morato'
- 'Baharan Mirzasoleiman'
year: 2026
month: 11
arxiv_id: '2611.00554'
url: https://arxiv.org/abs/2611.00554
methods:
- method:sftprobe
cites:
- paper:olmo-3
tags:
- sft
- data-selection
- active
---

# From Weeks to Hours: Fast and Principled SFT Data Generation for Reasoning LLMs

## Abstract Summary
Reasoning SFT usually generates huge teacher-trace pools then filters with more LLMs. SFTProbe predicts difficulty and diversity from a brief LoRA adaptation plus loss on 5% of each trace, using a geometric view of a low-rank anisotropic loss basin. NeurIPS 2026.

## Key Contributions
1. LoRA-probe SFT data selection that skips generate-then-filter teacher pools.

## Empirical Highlights
5k selected traces match 89k OpenThoughts-Math; 7.5k add +2.5%. Curation weeks to hours. Project bigml-cs-ucla.github.io/SFTProbe-page/.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.00554`
- Project: `https://bigml-cs-ucla.github.io/SFTProbe-page/`. Code: none found (`code_status: none`).
