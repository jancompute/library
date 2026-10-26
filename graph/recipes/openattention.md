---
id: recipe:openattention
type: recipe
title: 'OpenAttention'
method: method:openattention
task: task:posttrain-attention-sparsification
target_hardware: 'Paper: sparse attention at 1-5% KV reads'
framework: PyTorch
repo_url: https://github.com/hyunwoo137/OpenAttention
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- openattention
---

# OpenAttention

## Hardware & Environment Setup
- Official: `https://github.com/hyunwoo137/OpenAttention`.
- `code_status: released` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def tail_proxy(unread):
    if not unread:
        raise ValueError('tail')
    n = len(unread)
    return tuple(sum(x) / n for x in zip(*unread))
```

Do not retarget locked SOTA from this recipe.
