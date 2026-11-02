---
id: recipe:muon-rt
type: recipe
title: 'Muon-RT'
method: method:muon-rt
task: task:llm-pretraining-optimization
target_hardware: 'Paper: 7B SDFT / SDPO'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- muon-rt
---

# Muon-RT

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-02.

## Quickstart Implementation

```python
from __future__ import annotations

def muon_rt_buf(teacher_w, student_w, grad, mix=0.5):
    disp = student_w - teacher_w
    radial = (disp * student_w).sum() / student_w.pow(2).sum().clamp_min(1e-8)
    tangent = disp - radial * student_w
    return mix * tangent + (1.0 - mix) * grad
```

Do not retarget locked SOTA from this recipe.
