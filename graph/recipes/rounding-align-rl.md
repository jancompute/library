---
id: recipe:rounding-align-rl
type: recipe
title: 'Rounding-Align RL'
method: method:rounding-align-rl
task: task:fp4-rl-train-rollout-alignment
target_hardware: 'Paper: split inference/train LLM RL in BF16'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- rounding-align-rl
---

# Rounding-Align RL

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def round_at(x: float, where: str) -> str:
    if where not in {'pre', 'post'}:
        raise ValueError('where')
    return where
```

Do not retarget locked SOTA from this recipe.
