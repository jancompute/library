---
id: recipe:sifr
type: recipe
title: 'SIFR'
method: method:sifr
task: task:posttrain-diffusion
target_hardware: 'Paper: SD3.5-M 2.5B / FLUX.2 Klein 9B / Cosmos 3 Super T2I 64B'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- sifr
---

# SIFR

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-09.

## Quickstart Implementation

```python
from __future__ import annotations

def sifr_signed_adv(reward, group_mean):
    return 1.0 if reward >= group_mean else -1.0
```

Do not retarget locked SOTA from this recipe.
