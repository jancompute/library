---
id: recipe:steer-teacher
type: recipe
title: 'Steered-Teacher OPSD'
method: method:steer-teacher
task: task:privileged-teacher-opsd
target_hardware: 'Paper: privileged OPSD on thinking models'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- steer-teacher
---

# Steered-Teacher OPSD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def steer(h, cite_dir, recon_dir, a: float = 1.0, b: float = 1.0):
    return [x - a * c + b * r for x, c, r in zip(h, cite_dir, recon_dir)]
```

Do not retarget locked SOTA from this recipe.
