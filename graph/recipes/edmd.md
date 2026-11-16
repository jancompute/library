---
id: recipe:edmd
type: recipe
title: eDMD
method: method:edmd
task: task:posttrain-diffusion
target_hardware: 'Paper: 4-step distill of SD3-Medium / FLUX.2-klein / Qwen-Image'
framework: PyTorch
repo_url: https://github.com/Westlake-AGI-Lab/eDMD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- edmd
---

# eDMD

## Hardware & Environment Setup
- Official: `https://github.com/Westlake-AGI-Lab/eDMD` (`code_status: released`).
- Train the fake score only on student final outputs. Precise teacher is a short multi-step on the final noise interval. No real images.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def edmd_fake_loss(fake: torch.Tensor, student_endpoint: torch.Tensor) -> torch.Tensor:
    return F.mse_loss(fake, student_endpoint.detach())
```

Do not retarget locked SOTA from this recipe.
