---
id: recipe:uni-mopd
type: recipe
title: Uni-MOPD
method: method:uni-mopd
task: task:student-distillation
target_hardware: 'Paper: Qwen3-VL-30B-A3B, five multimodal domains / 19 benches'
framework: PyTorch
repo_url: https://huggingface.co/AmberHeart/Uni-MOPD
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- uni-mopd
---

# Uni-MOPD

## Hardware & Environment Setup
- Checkpoints: `https://huggingface.co/AmberHeart/Uni-MOPD`
- `code_status: announced` as of 2026-11-26. Train framework will be released. Paper Open-MOPD is not the library 83.4% bake-off. Does not replace Open-MOPD.

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


def uniform_teacher_kl(per_teacher_kls: list[torch.Tensor]) -> torch.Tensor:
    return torch.stack(per_teacher_kls).mean()
```
