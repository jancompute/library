---
id: recipe:wid
type: recipe
title: 'WiD'
method: method:wid
task: task:pixel-diffusion-pretrain
target_hardware: 'Paper: PixelDiT-XL / DeCo-XXL pixel-space flow'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- wid
---

# WiD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-29.

## Quickstart Implementation

```python
from __future__ import annotations

def wid_velocity(wiener_branch, coeff_correction, pixel_head):
    return wiener_branch + coeff_correction + pixel_head
```

Do not retarget locked SOTA from this recipe.
