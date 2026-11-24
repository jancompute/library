---
id: recipe:vopd
type: recipe
title: VOPD
method: method:vopd
task: task:student-distillation
target_hardware: 'Paper: Qwen3-4B / 1.7B, extra frozen-reference pass'
framework: PyTorch
repo_url: https://github.com/juntongshi48/VOPD
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- vopd
---

# VOPD

## Hardware & Environment Setup
- Official: `https://github.com/juntongshi48/VOPD`
- `code_status: announced` as of 2026-11-24 (README: code will be released soon). Verifier-grounded teacher extrapolation at \(\lambda=0.25\). Distinct from OPDVR. Does not replace OPD.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def vopd_target(teacher_logp: torch.Tensor, ref_logp: torch.Tensor, advantage: torch.Tensor, lam: float = 0.25) -> torch.Tensor:
    return teacher_logp + lam * advantage.detach() * (teacher_logp - ref_logp).detach()
```
