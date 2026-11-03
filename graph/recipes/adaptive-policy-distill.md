---
id: recipe:adaptive-policy-distill
type: recipe
title: 'Adaptive-Policy Distillation'
method: method:adaptive-policy-distill
task: task:student-distillation
target_hardware: 'Paper: document-QA knowledge injection'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- adaptive-policy-distill
---

# Adaptive-Policy Distillation

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def apd_gate(student_logp, teacher_logp, thresh):
    hard = (teacher_logp - student_logp).abs() > thresh
    return hard.float()
```

Do not retarget locked SOTA from this recipe.
