---
id: recipe:data-constrained-hp-ensemble
type: recipe
title: 'Data-Constrained HP Transfer + Ensemble'
method: method:data-constrained-hp-ensemble
task: task:data-constrained-pretrain
target_hardware: 'Paper: FineWeb 100M unique tokens'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- data-constrained-hp-ensemble
---

# Data-Constrained HP Transfer + Ensemble

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def transfer_wd(wd0, n_params, n_params0, epochs):
    return wd0 * ((n_params / n_params0) ** 0.5) * (epochs ** 0.5)
```

Do not retarget locked SOTA from this recipe.
