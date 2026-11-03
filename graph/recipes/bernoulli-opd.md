---
id: recipe:bernoulli-opd
type: recipe
title: 'Bernoulli OPD'
method: method:bernoulli-opd
task: task:student-distillation
target_hardware: 'Paper: sampled-token OPD students'
framework: PyTorch
repo_url: https://github.com/duterscmy/Bernoulli-OPD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- bernoulli-opd
---

# Bernoulli OPD

## Hardware & Environment Setup
- Official: `https://github.com/duterscmy/Bernoulli-OPD`.
- `code_status: released` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def bernoulli_opd(student_p, teacher_p):
    return teacher_p - student_p
```

Do not retarget locked SOTA from this recipe.
