---
id: recipe:steerdistill
type: recipe
title: 'SteerDistill'
method: method:steerdistill
task: task:full-lowbit-finetune
target_hardware: 'Paper: Qwen3-8B W4A16 student, frozen BF16 teacher, agent rollouts'
framework: PyTorch
repo_url: https://github.com/air-embodied-brain/SteerDistill
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- steerdistill
---

# SteerDistill

## Hardware & Environment Setup
- Official: `https://github.com/air-embodied-brain/SteerDistill` (`code_status: released`).
- Frozen BF16 teacher of the same checkpoint. Align student/teacher by environment transitions, not action strings.

## Quickstart Implementation

```python
from __future__ import annotations

def first_divergence(student_transitions, teacher_transitions) -> int:
    n = min(len(student_transitions), len(teacher_transitions))
    return next((i for i in range(n) if student_transitions[i] != teacher_transitions[i]), n)
```

Do not retarget locked SOTA from this recipe.
