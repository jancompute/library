---
id: recipe:lora-init-asymmetric
type: recipe
title: 'LoRA Init Asymmetric'
method: method:lora-init-asymmetric
task: task:lora-quality-tuning
target_hardware: 'Paper: LoRA / LoRA+ LR sweeps'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- lora-init-asymmetric
---

# LoRA Init Asymmetric

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def scale_b(rank: int, alpha: float) -> float:
    if rank <= 0:
        raise ValueError('rank')
    return alpha / float(rank)
```

Do not retarget locked SOTA from this recipe.
