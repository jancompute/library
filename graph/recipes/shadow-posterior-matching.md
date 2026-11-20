---
id: recipe:shadow-posterior-matching
type: recipe
title: Shadow Posterior Matching
method: method:shadow-posterior-matching
task: task:posttrain-diffusion
target_hardware: 'Paper: 4-step SD3.5-Medium LoRA, 8×H100, 1,000 steps'
framework: PyTorch
repo_url: https://github.com/shadow-posterior/code
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- shadow-posterior
---

# Shadow Posterior Matching

## Hardware & Environment Setup
- Official: `https://github.com/shadow-posterior/code`
- `code_status: released` as of 2026-11-20. 4-step SD3.5-Medium LoRA recipes (`configs/sd35m_geneval.yaml`, OCR). Distinct from `method:bpo` (Policy Mirror Descent). Does not replace DiffusionOPSD.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def shadow_credit(
    fake_score: torch.Tensor,
    generator_out: torch.Tensor,
    teacher_out: torch.Tensor,
    advantage: torch.Tensor,
    residual_weight: torch.Tensor,
    alpha: float = 0.1,
) -> torch.Tensor:
    reward_dir = residual_weight.unsqueeze(-1) * advantage.unsqueeze(-1) * (generator_out - fake_score)
    teacher_kl = F.mse_loss(generator_out, teacher_out)
    endpoint = F.mse_loss(generator_out, fake_score.detach())
    return (reward_dir.pow(2).mean() + alpha * teacher_kl + alpha * endpoint)
```
