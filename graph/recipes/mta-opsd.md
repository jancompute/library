---
id: recipe:mta-opsd
type: recipe
title: 'MTA-OPSD'
method: method:mta-opsd
task: task:privileged-teacher-opsd
target_hardware: 'Paper: token-level privileged OPSD'
framework: PyTorch
repo_url: https://github.com/xingzhejun/MTA-OPSD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- mta-opsd
---

# MTA-OPSD

## Hardware & Environment Setup
- Official: `https://github.com/xingzhejun/MTA-OPSD`.
- `code_status: released` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def mta_pick(teacher_logps, student_logp):
    kls = [(t - student_logp).abs().mean() for t in teacher_logps]
    return int(min(range(len(kls)), key=lambda i: kls[i]))
```

Do not retarget locked SOTA from this recipe.
