---
id: recipe:roar
type: recipe
title: 'RoAR'
method: method:roar
task: task:math-code-rl-dense
target_hardware: 'Paper: GRPO rollout agreement'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- roar
---

# RoAR

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def roar(r: float, agree: float, w: float = 0.1) -> float:
    return r + (w * agree if r > 0 else 0.0)
```

Do not retarget locked SOTA from this recipe.
