---
id: paper:muon-rt
type: paper
title: 'MUON-RT Reusing the Teacher''s Trajectory for Momentum-Free Muon for LLM Self-Distillation'
authors:
- 'Aryan Das'
- 'Vinay Kumar Verma'
- 'Aakansha Mishra'
year: 2026
month: 10
arxiv_id: '2610.41104'
url: https://arxiv.org/abs/2610.41104
methods:
- method:muon-rt
cites:
- paper:muon2
- paper:opd
tags:
- muon
- distillation
- active
---

# MUON-RT Reusing the Teacher's Trajectory for Momentum-Free Muon for LLM Self-Distillation

## Abstract Summary
EMA-teacher self-distillation already stores a history of student updates, so Muon's extra momentum buffer is redundant memory. Muon-RT reuses the teacher-student displacement for hidden matrices: drop the radial component, spectrally normalize, mix with the current gradient after Newton-Schulz. On Qwen2.5-7B-Instruct SDFT it beats AdamW by 2.6 points with 42% less persistent memory and momentum Muon by 5.4 with 27% less. On Olmo-3-7B-Instruct SDPO it beats AdamW by 2.0.

## Key Contributions
1. Momentum-free Muon that reuses EMA teacher-student displacement during self-distillation.

## Empirical Highlights
No public code as of 2026-11-02. Does not retarget method:muon2 or method:opd.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.41104`
- Code: none found (`code_status: none`).
