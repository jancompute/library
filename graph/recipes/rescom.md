---
id: recipe:rescom
type: recipe
title: 'ResCom'
method: method:rescom
task: task:fp4-hardware-training
target_hardware: 'Paper: Llama-3-8B W4A4 PTQ'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- rescom
---

# ResCom

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def residual_dir(rounding_error, output_grad):
    return rounding_error * output_grad
```

Do not retarget locked SOTA from this recipe.
