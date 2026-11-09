---
id: recipe:p2-mopd
type: recipe
title: 'P2-MOPD'
method: method:p2-mopd
task: task:student-distillation
target_hardware: 'Paper: 1.7B / 4B four-domain MOPD'
framework: PyTorch
repo_url: https://github.com/SinuoWang/P2-MOPD
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- p2-mopd
---

# P2-MOPD

## Hardware & Environment Setup
- Announced: `https://github.com/SinuoWang/P2-MOPD`.
- `code_status: announced` as of 2026-11-09 (README-only).

## Quickstart Implementation

```python
from __future__ import annotations

def p2_mopd_mix(student, experts, coef):
    out = student
    for c, e in zip(coef, experts):
        out = out + c * (e - student)
    return out
```

Do not retarget locked SOTA from this recipe.
