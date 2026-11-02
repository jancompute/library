---
id: recipe:uploop
type: recipe
title: 'UpLoop'
method: method:uploop
task: task:elastic-depth-looped-lm
target_hardware: 'Paper: dense looped pretrain through 1.3B'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- uploop
---

# UpLoop

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-02.

## Quickstart Implementation

```python
from __future__ import annotations

def uploop_schedule(step, copy_until, loop_after):
    if step < copy_until:
        return "grow"
    if step >= loop_after:
        return "loop_middle"
    return "train"
```

Do not retarget locked SOTA from this recipe.
