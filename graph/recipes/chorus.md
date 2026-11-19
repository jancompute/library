---
id: recipe:chorus
type: recipe
title: Chorus
method: method:chorus
task: task:pretrain-dense-7b
target_hardware: 'Paper: 17.1M–9.6B ClimbMix/FineWeb/DCLM n-gram tables'
framework: PyTorch
repo_url: https://github.com/dualverse-ai/chorous
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- chorus
---

# Chorus

## Hardware & Environment Setup
- Official: `https://github.com/dualverse-ai/chorous` (typo in repo name).
- `code_status: released` as of 2026-11-19. Shared n-gram tables plus per-layer rescale/project. Ember compresses table optimizer state. Does not replace Muon2.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn as nn


class ChorusLayerAdapt(nn.Module):
    def __init__(self, dim: int) -> None:
        super().__init__()
        self.scale = nn.Parameter(torch.ones(dim))
        self.proj = nn.Linear(dim, dim, bias=False)

    def forward(self, table_lookup: torch.Tensor) -> torch.Tensor:
        return self.proj(table_lookup * self.scale)
```

Do not retarget locked SOTA from this recipe.
