---
id: recipe:lazyflash
type: recipe
title: 'LazyFlash'
method: method:lazyflash
task: task:posttrain-attention-sparsification
target_hardware: 'Paper: long-context LLM fine-tuning'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- lazyflash
---

# LazyFlash

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def backward_keep(n: int, k: int) -> int:
    if n <= 0 or k <= 0:
        raise ValueError('k')
    return min(n, k)
```

Do not retarget locked SOTA from this recipe.
