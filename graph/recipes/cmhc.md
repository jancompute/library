---
id: recipe:cmhc
type: recipe
title: cmHC
method: method:cmhc
task: task:llm-pretraining-optimization
target_hardware: 'Paper: nanoGPT 8xH100; fused kernels on Ascend 910C'
framework: PyTorch
repo_url: https://github.com/Newiz430/cmHC
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- cmhc
---

# cmHC

## Hardware & Environment Setup
- Official: `https://github.com/Newiz430/cmHC`
- `code_status: released` as of 2026-11-23. Contract mHC-lite permutation bases with \(\lambda=0.97\) on the first \(K=2\) layers. Does not replace Muon2 or mHC.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def contract_permutation(perm: torch.Tensor, lam: float = 0.97) -> torch.Tensor:
    n = perm.shape[-1]
    barycenter = torch.full_like(perm, 1.0 / n)
    return lam * perm + (1.0 - lam) * barycenter
```
