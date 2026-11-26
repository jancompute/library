---
id: recipe:care-opd
type: recipe
title: CARE-OPD
method: method:care-opd
task: task:student-distillation
target_hardware: 'Paper: SWE-bench Verified agentic OPD vs async online OPD'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- care-opd
---

# CARE-OPD

## Hardware & Environment Setup
- `code_status: none` as of 2026-11-26. Prefix-replay OPD with confidence gating and hindsight allocation. Distinct from `method:care-po`. Does not replace OPD or CANOPY.

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


def confidence_gate(teacher_logp: torch.Tensor, student_logp: torch.Tensor, tau: float) -> torch.Tensor:
    return (teacher_logp - student_logp) > tau
```
