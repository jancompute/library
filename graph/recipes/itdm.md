---
id: recipe:itdm
type: recipe
title: iTDM
method: method:itdm
task: task:posttrain-diffusion
target_hardware: 'Paper: SD3.5-M GenEval2; FLUX.3 5.6B'
framework: PyTorch
repo_url: https://github.com/Luo-Yihong/iTDM
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- itdm
---

# iTDM

## Hardware & Environment Setup
- Official: `https://github.com/Luo-Yihong/iTDM`
- `code_status: released` as of 2026-11-25. Auxiliary denoiser tracks the behavior velocity. Does not replace DiffusionOPSD or Self-OPD.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def itdm_grad(
    v_theta: torch.Tensor,
    v_aux: torch.Tensor,
    advantage: torch.Tensor,
) -> torch.Tensor:
    residual = v_theta - v_aux.detach()
    return (advantage.view(-1, 1, 1, 1) * residual).mean()
```
