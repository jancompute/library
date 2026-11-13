---
id: recipe:simplehc
type: recipe
title: SimpleHC
method: method:simplehc
task: task:llm-pretraining-optimization
target_hardware: 'Paper: 15B/30B MoE Hyper-Connection pretrain'
framework: PyTorch
repo_url: https://github.com/aHapBean/SimpleHC
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- simplehc
---

# SimpleHC

## Hardware & Environment Setup
- Official: `https://github.com/aHapBean/SimpleHC` (`code_status: announced`; README + paper PDF as of 2026-11-13).
- Keep learned read/write gates. Drop residual mixing. Share the residual-stream buffer. Do not retarget mHC or DeepSeek-V4.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def simplehc_write(memory: torch.Tensor, update: torch.Tensor, gate: torch.Tensor) -> torch.Tensor:
    w = torch.sigmoid(gate)
    return memory + w * (update - memory)
```

Do not retarget locked SOTA from this recipe.
