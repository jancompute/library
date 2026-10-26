---
id: recipe:datc
type: recipe
title: 'DATC'
method: method:datc
task: task:math-code-rl-dense
target_hardware: 'Paper: GRPO-host token credit with an RM'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- datc
---

# DATC

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def work(force, disp) -> float:
    if len(force) != len(disp):
        raise ValueError('dim')
    return sum(a * b for a, b in zip(force, disp))
```

Do not retarget locked SOTA from this recipe.
