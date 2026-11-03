---
id: recipe:self-steered-reasoner
type: recipe
title: 'Self-Steered Reasoner'
method: method:self-steered-reasoner
task: task:privileged-teacher-opsd
target_hardware: 'Paper: reasoning RL then privileged self-distill'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- self-steered-reasoner
---

# Self-Steered Reasoner

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def student_support_project(teacher_logits, student_probs, k=16):
    keep = student_probs.topk(k).indices
    return teacher_logits.scatter(1, keep, teacher_logits.gather(1, keep))
```

Do not retarget locked SOTA from this recipe.
