---
id: recipe:contrastive-opd
type: recipe
title: cOPD
method: method:contrastive-opd
task: task:student-distillation
target_hardware: 'Paper: Qwen3-4B / Llama-3.2-3B students, dual teachers'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- contrastive-opd
---

# cOPD

## Hardware & Environment Setup
- `code_status: none` as of 2026-11-24. No public GitHub. Dual-branch strong/weak teacher contrast. MUST NOT reuse slug `copd`. Does not replace OPD.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def copd_weight(delta: torch.Tensor, tau: float = 1.0) -> torch.Tensor:
    return torch.tanh(delta / tau)
```
