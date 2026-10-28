---
id: recipe:mpopd
type: recipe
title: 'MPOPD'
method: method:mpopd
task: task:student-distillation
target_hardware: 'Paper: Qwen3-4B-Base OPD'
framework: PyTorch
repo_url: https://github.com/csr16/MPOPD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- mpopd
---

# MPOPD

## Hardware & Environment Setup
- Official: `https://github.com/csr16/MPOPD`.
- `code_status: released` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def mixture_logp(student_logp, teacher_logp, lam=0.5):
    return lam * student_logp + (1.0 - lam) * teacher_logp
```

Do not retarget locked SOTA from this recipe.
