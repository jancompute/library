---
id: recipe:scalerlt
type: recipe
title: 'ScaleRLT'
method: method:scalerlt
task: task:recurrent-encoder-decoder-lm
target_hardware: 'Paper: looped-transformer GRPO'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- scalerlt
---

# ScaleRLT

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def hybrid_logp(dense: float, sched: float) -> float:
    return dense + (sched - dense)
```

Do not retarget locked SOTA from this recipe.
