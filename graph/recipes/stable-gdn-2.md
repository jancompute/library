---
id: recipe:stable-gdn-2
type: recipe
title: Stable GDN-2
method: method:stable-gdn-2
task: task:linear-time-sequence-modeling
target_hardware: 'Paper: 1.6B recurrent/hybrid GDN-2, 64K pretrain'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- stable-gdn-2
---

# Stable GDN-2

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-27.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def symmetric_erase_keys(k: torch.Tensor, erase_gate: torch.Tensor) -> tuple[torch.Tensor, torch.Tensor]:
    half = erase_gate.clamp(0.0, 1.0).sqrt()
    return half * k, half * k


def decay_regulated_write(write_gate: torch.Tensor, decay: torch.Tensor) -> torch.Tensor:
    return write_gate + (1.0 - write_gate) * decay.clamp(0.0, 1.0)
```

Do not retarget locked SOTA from this recipe.
