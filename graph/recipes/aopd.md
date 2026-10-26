---
id: recipe:aopd
type: recipe
title: 'AOPD'
method: method:aopd
task: task:student-distillation
target_hardware: 'Paper: on-policy student distillation'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- aopd
---

# AOPD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def follow_teacher(adv: float, floor: float = 0.0) -> bool:
    return adv > floor
```

Do not retarget locked SOTA from this recipe.
