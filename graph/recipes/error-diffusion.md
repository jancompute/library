---
id: recipe:error-diffusion
type: recipe
title: 'Error-Diffusion Binary Weights'
method: method:error-diffusion
task: task:1bit-extreme-quantization
target_hardware: 'Paper: binary-weight residual buffers'
framework: PyTorch
repo_url: https://github.com/pierreolivierbonin/error-diffusion-binary-weight-lms
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- error-diffusion
---

# Error-Diffusion Binary Weights

## Hardware & Environment Setup
- Official: `https://github.com/pierreolivierbonin/error-diffusion-binary-weight-lms`.
- `code_status: released` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def ed_step(w: int, residual: float, g: float, thr: float = 0.5) -> tuple[int, float]:
    residual += g
    if residual >= thr:
        return 1, residual - 1.0
    if residual <= -thr:
        return -1, residual + 1.0
    return w, residual
```

Do not retarget locked SOTA from this recipe.
