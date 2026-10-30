---
id: recipe:scarl
type: recipe
title: 'SCARL'
method: method:scarl
task: task:math-code-rl-dense
target_hardware: 'Paper: sequence-level RLVR'
framework: PyTorch
repo_url: https://github.com/kezhh163/scarl
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- scarl
---

# SCARL

## Hardware & Environment Setup
- Official: `https://github.com/kezhh163/scarl`.
- `code_status: released` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def scarl_reshape(adv, conf):
    gap = (conf - conf.mean()) * adv.sign()
    scale = (adv.abs() * (1.0 + gap)).clamp_min(0)
    return adv.sign() * scale
```

Do not retarget locked SOTA from this recipe.
