---
id: recipe:state-kl-opd
type: recipe
title: State-KL OPD
method: method:state-kl-opd
task: task:student-distillation
target_hardware: 'Paper: Qwen3-1.7B/4B/8B students, Qwen3-8B teacher'
framework: PyTorch
repo_url: https://github.com/zhangxinnan123/learning-dynamic-opd
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- state-kl-opd
---

# State-KL OPD

## Hardware & Environment Setup
- Official: `https://github.com/zhangxinnan123/learning-dynamic-opd`
- `code_status: released` as of 2026-11-23. Forward KL when student coverage of the teacher top-p set is low. Does not replace OPD.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def use_forward_kl(
    student_on_teacher_top: torch.Tensor,
    teacher_mass_under: torch.Tensor,
    cover_min: float = 0.3,
    under_max: float = 0.2,
) -> torch.Tensor:
    return (student_on_teacher_top < cover_min) | (teacher_mass_under > under_max)
```
