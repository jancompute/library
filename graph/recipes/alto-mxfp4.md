---
id: recipe:alto-mxfp4
type: recipe
title: 'ALTO MXFP4'
method: method:alto-mxfp4
task: task:fp4-hardware-training
target_hardware: 'Paper: GPT-OSS-20B MXFP4 / MLPerf Small MoE'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- alto-mxfp4
---

# ALTO MXFP4

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def mxfp4_ok(scale: float, floor: float) -> bool:
    if scale <= 0:
        raise ValueError('scale')
    return scale >= floor
```

Do not retarget locked SOTA from this recipe.
