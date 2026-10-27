---
id: recipe:doublefree
type: recipe
title: 'DoubleFree'
method: method:doublefree
task: task:student-distillation
target_hardware: 'Paper: rollout-free multi-task distill'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- doublefree
---

# DoubleFree

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def reuse(trace: list, teacher_logp: list) -> list:
    return list(zip(trace, teacher_logp))
```

Do not retarget locked SOTA from this recipe.
