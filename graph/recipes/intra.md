---
id: recipe:intra
type: recipe
title: 'INTRA'
method: method:intra
task: task:posttrain-attention-sparsification
target_hardware: 'Paper: CQS-aware Flash sparse attention'
framework: PyTorch
repo_url: https://github.com/NovTi/INTRA
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- intra
---

# INTRA

## Hardware & Environment Setup
- Official: `https://github.com/NovTi/INTRA`.
- `code_status: released` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def scatter_stride(n: int, g: int) -> list[int]:
    return list(range(0, n, max(g, 1)))
```

Do not retarget locked SOTA from this recipe.
