---
id: recipe:sparse-teacher-support
type: recipe
title: Sparse Teacher Support
method: method:sparse-teacher-support
task: task:student-distillation
target_hardware: 'Paper: Qwen3 4B→1.7B forward-KL; Nemotron Nano support-floor check'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- sparse-teacher-support
---

# Sparse Teacher Support

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-13. Cache teacher top-$k$ scores. Renormalize the kept mass. Keep $k$ large enough that the student still emits the closing reasoning tag.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def sparse_teacher_fkl(student_logits: torch.Tensor, teacher_top_logp: torch.Tensor, teacher_idx: torch.Tensor) -> torch.Tensor:
    student_logp = F.log_softmax(student_logits, dim=-1)
    gathered = student_logp.gather(-1, teacher_idx)
    teacher_p = teacher_top_logp.exp()
    teacher_p = teacher_p / teacher_p.sum(dim=-1, keepdim=True)
    return -(teacher_p * gathered).sum(dim=-1).mean()
```

Do not retarget locked SOTA from this recipe.
