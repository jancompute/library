---
id: recipe:bred
type: recipe
title: BReD
method: method:bred
task: task:full-param-memory-efficient-pretrain
target_hardware: 'Paper: 120M–3.4B pretrain, 7B FT; 4-bit EMA states'
framework: PyTorch
repo_url: https://github.com/ZhanHeshen/BReD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- bred
---

# BReD

## Hardware & Environment Setup
- Official: `https://github.com/ZhanHeshen/BReD`.
- `code_status: released` as of 2026-11-27.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def block_dither(seed: int, block_id: int) -> float:
    g = torch.Generator()
    g.manual_seed((seed ^ (block_id * 0x9E3779B9)) & 0xFFFFFFFF)
    return float(torch.rand(1, generator=g) - 0.5)


def bred_quantize(x: torch.Tensor, scale: float, dither: float, nbits: int = 4) -> torch.Tensor:
    qmax = (1 << (nbits - 1)) - 1
    return ((x / scale + dither).round().clamp(-qmax, qmax))


def bred_dequantize(q: torch.Tensor, scale: float, dither: float) -> torch.Tensor:
    return (q - dither) * scale
```

Do not retarget locked SOTA from this recipe.
