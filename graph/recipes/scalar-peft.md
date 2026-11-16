---
id: recipe:scalar-peft
type: recipe
title: SCALAR
method: method:scalar-peft
task: task:lora-quality-tuning
target_hardware: 'Paper: Qwen2.5-7B / LLaMA3-8B commonsense PEFT'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- scalar-peft
---

# SCALAR

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-16. Freeze an activation-derived input basis and a random output dictionary. Train only layer-specific scalars.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn as nn


class ScalarAdapter(nn.Module):
    def __init__(self, n_layers: int) -> None:
        super().__init__()
        self.scale = nn.Parameter(torch.ones(n_layers))

    def forward(self, basis: torch.Tensor, dictionary: torch.Tensor, layer: int) -> torch.Tensor:
        return self.scale[layer] * (basis @ dictionary)
```

Do not retarget locked SOTA from this recipe.
