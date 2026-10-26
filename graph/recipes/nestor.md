---
id: recipe:nestor
type: recipe
title: 'NESTOR'
method: method:nestor
task: task:pretrain-dense-7b
target_hardware: 'Paper: nested-sparsity pretrain / continual learning'
framework: PyTorch
repo_url: https://github.com/Ma-Lab-Berkeley/Nestor
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- nestor
---

# NESTOR

## Hardware & Environment Setup
- Official: `https://github.com/Ma-Lab-Berkeley/Nestor`.
- `code_status: released` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def nest_keep(level: int, width: int) -> int:
    if level < 0 or width <= 0:
        raise ValueError('nest')
    return max(1, width // (2 ** level))
```

Do not retarget locked SOTA from this recipe.
