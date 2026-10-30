---
id: recipe:idm
type: recipe
title: 'IDM'
method: method:idm
task: task:posttrain-diffusion
target_hardware: 'Paper: Z-Image-Turbo 6B / Qwen-Image 20B'
framework: PyTorch
repo_url: https://github.com/inclusionAI/IDM
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- idm
---

# IDM

## Hardware & Environment Setup
- Official: `https://github.com/inclusionAI/IDM`.
- `code_status: released` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def idm_moment(feat, ema_feat):
    return (feat.mean() - ema_feat.mean()).pow(2) + (feat.std() - ema_feat.std()).pow(2)
```

Do not retarget locked SOTA from this recipe.
