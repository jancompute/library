---
id: recipe:op-self-training
type: recipe
title: 'On-Policy Self-Training'
method: method:op-self-training
task: task:data-free-self-evolution
target_hardware: 'Paper: data-free on-policy self-training'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- op-self-training
---

# On-Policy Self-Training

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def keep_pair(q: str, a: str) -> bool:
    if not q or not a:
        raise ValueError('qa')
    return True
```

Do not retarget locked SOTA from this recipe.
