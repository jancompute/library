---
id: recipe:loco
type: recipe
title: 'LoCo'
method: method:loco
task: task:math-code-rl-dense
target_hardware: 'Paper: math/code RLVR length control'
framework: PyTorch
repo_url: https://github.com/MuyaoYuan/LoCo
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- loco
---

# LoCo

## Hardware & Environment Setup
- Official: `https://github.com/MuyaoYuan/LoCo`.
- `code_status: released` as of 2026-11-04.

## Quickstart Implementation

```python
from __future__ import annotations

def loco_pair(prefix, continue_tok, stop_tok):
    return prefix, continue_tok, stop_tok
```

Do not retarget locked SOTA from this recipe.
