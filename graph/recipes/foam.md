---
id: recipe:foam
type: recipe
title: FOAM
method: method:foam
task: task:llm-pretraining-optimization
target_hardware: 'Paper: 124M–760M dense transformer pretrain; SOAP-memory constrained GPUs'
framework: PyTorch
repo_url: https://github.com/naver-ai/foam
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- foam
---

# FOAM

## Hardware & Environment Setup
- Official: `https://github.com/naver-ai/foam` (`code_status: announced`; README-only as of 2026-11-13).
- Keep SOAP on the input Gram only. Factor Adam's second moment with the same Kronecker factors. Do not retarget Muon2 or KL-SOAP.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def foam_precondition(grad: torch.Tensor, l_in: torch.Tensor) -> torch.Tensor:
    g = grad.reshape(grad.shape[0], -1)
    return (l_in @ g).reshape(grad.shape)
```

Do not retarget locked SOTA from this recipe.
