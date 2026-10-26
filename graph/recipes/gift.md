---
id: recipe:gift
type: recipe
title: 'GIFT'
method: method:gift
task: task:student-distillation
target_hardware: 'Paper: distillation-augmented reasoning RL'
framework: PyTorch
repo_url: https://github.com/lilifree/GIFT
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- gift
---

# GIFT

## Hardware & Environment Setup
- Official: `https://github.com/lilifree/GIFT`.
- `code_status: released` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def keep_if_aligned(distill_g, rl_g, eps: float = 0.0) -> bool:
    if not distill_g or not rl_g:
        raise ValueError('grads')
    return sum(a * b for a, b in zip(distill_g, rl_g)) > eps
```

Do not retarget locked SOTA from this recipe.
