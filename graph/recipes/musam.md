---
id: recipe:musam
type: recipe
title: 'Sharpness-Aware Muon (MuSAM / MoMuSAM)'
method: method:musam
task: task:llm-pretraining-optimization
target_hardware: 'Paper: sharpness-aware Muon ablations'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- musam
---

# Sharpness-Aware Muon (MuSAM / MoMuSAM)

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def momusam_perturb(momentum, rho=0.05):
    norm = (momentum * momentum).sum() ** 0.5
    return rho * momentum / (norm + 1e-12)
```

Do not retarget locked SOTA from this recipe.
