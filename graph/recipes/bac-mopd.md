---
id: recipe:bac-mopd
type: recipe
title: BaC-MOPD
method: method:bac-mopd
task: task:student-distillation
target_hardware: 'Paper: industrial six-specialist; open Qwen3-4B five-domain'
framework: PyTorch
repo_url: announced
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- bac-mopd
---

# BaC-MOPD

## Hardware & Environment Setup
- `code_status: announced` as of 2026-11-25. Merge init, error-replay queries, frozen self-teacher, per-teacher then equal-across-teachers reverse-KL. Paper IM-MOPD numbers are not the library 83.4% bake-off. Does not replace Open-MOPD.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def reverse_kl(student_logits: torch.Tensor, teacher_logits: torch.Tensor) -> torch.Tensor:
    log_p = F.log_softmax(student_logits, dim=-1)
    log_q = F.log_softmax(teacher_logits, dim=-1)
    p = log_p.exp()
    return (p * (log_p - log_q)).sum(dim=-1).mean()


def bac_mopd_loss(
    per_teacher_kls: list[torch.Tensor],
    self_teacher_kl: torch.Tensor,
    alpha: float = 0.1,
) -> torch.Tensor:
    stacked = torch.stack([kl.mean() for kl in per_teacher_kls])
    return stacked.mean() + alpha * self_teacher_kl
```
