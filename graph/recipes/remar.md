---
id: recipe:remar
type: recipe
title: ReMaRL
method: method:remar
task: task:diffusion-lm-ar-delta-recycle
target_hardware: 'Paper: LLaDA-8B-Instruct / Dream-v0-Instruct-7B frozen dLLM + 0.3M GRPO policy'
framework: PyTorch
repo_url: https://github.com/EgorShibaev/remarl
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- remar
---

# ReMaRL

## Hardware & Environment Setup
- Official: `https://github.com/EgorShibaev/remarl` (`code_status: released`).
- Freeze the dLLM. Residual-correct P2′ position scores with GRPO. Choose unmask / retain / remask. Train a separate policy per NFE.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def remar_scores(p2_prime: torch.Tensor, residual: torch.Tensor) -> torch.Tensor:
    return p2_prime + residual
```

Do not retarget locked SOTA from this recipe.
