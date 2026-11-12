---
id: recipe:depthgraft
type: recipe
title: DepthGraft
method: method:depthgraft
task: task:llm-pretraining-optimization
target_hardware: 'Paper: 0.5B–16B dense and MoE, GQA and MLA'
framework: PyTorch
repo_url: https://github.com/jianke0604/DepthGraft
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- depthgraft
---

# DepthGraft

## Hardware & Environment Setup
- Official: `https://github.com/jianke0604/DepthGraft` (`code_status: released`).
- Apply hierarchical KV reconstruction during pretrain, not as a decode-only cache trick.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn as nn


class DepthGraftKV(nn.Module):
    def __init__(self, d_model: int, stride: int = 2) -> None:
        super().__init__()
        self.stride = stride
        self.recon = nn.Linear(2 * d_model, d_model)

    def reconstruct(self, shallow: torch.Tensor, middle: torch.Tensor) -> torch.Tensor:
        return self.recon(torch.cat([shallow, middle], dim=-1))
```

Do not retarget locked SOTA from this recipe.
