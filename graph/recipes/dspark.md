---
id: recipe:dspark
type: recipe
title: 'dSpark'
method: method:dspark
task: task:diffusion-lm-ar-delta-recycle
target_hardware: 'Paper: dLLM schedule distillation'
framework: PyTorch
repo_url: https://github.com/VILA-Lab/dSpark
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- dspark
---

# dSpark

## Hardware & Environment Setup
- Official: `https://github.com/VILA-Lab/dSpark`.
- `code_status: released` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def leverage(conf: float, remaining_drop: float) -> float:
    return remaining_drop - conf
```

Do not retarget locked SOTA from this recipe.
