---
id: recipe:order-only-opd
type: recipe
title: 'Order-Only OPD'
method: method:order-only-opd
task: task:student-distillation
target_hardware: 'Paper: six teacher-student pairs, AIME/HMMT'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- order-only-opd
---

# Order-Only OPD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def order_only_loss(student_logits, teacher_logits, k=16):
    order = teacher_logits.topk(k).indices
    return student_logits.gather(-1, order).neg().diff(dim=-1).clamp_min(0).mean()
```

Do not retarget locked SOTA from this recipe.
