---
id: recipe:gga-pw
type: recipe
title: 'GGA-PW'
method: method:gga-pw
task: task:linear-time-sequence-modeling
target_hardware: 'Paper: Gated DeltaNet recurrent-state quant'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- gga-pw
---

# GGA-PW

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def gga_bits(resid, grad, budget):
    score = (resid.abs() * grad.abs()).flatten()
    order = score.argsort(descending=True)
    return order[:budget]
```

Do not retarget locked SOTA from this recipe.
