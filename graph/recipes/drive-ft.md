---
id: recipe:drive-ft
type: recipe
title: 'DRIVE'
method: method:drive-ft
task: task:instruct-sft-alignment
target_hardware: 'Paper: single-stage FT without source data'
framework: PyTorch
repo_url: https://github.com/luciabcd/DRIVE
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- drive-ft
---

# DRIVE

## Hardware & Environment Setup
- Official: `https://github.com/luciabcd/DRIVE`.
- `code_status: released` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def mix_w(contrib: float, diversity: float) -> float:
    if contrib < 0 or diversity < 0:
        raise ValueError('w')
    return contrib * diversity
```

Do not retarget locked SOTA from this recipe.
