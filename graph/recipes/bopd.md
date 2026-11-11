---
id: recipe:bopd
type: recipe
title: 'BOPD'
method: method:bopd
task: task:privileged-teacher-opsd
target_hardware: 'Paper: Qwen3-4B/8B LoRA r=64, 100 steps/stage, batch 32'
framework: PyTorch
repo_url: https://github.com/YueWu0301/BOPD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- bopd
---

# BOPD

## Hardware & Environment Setup
- Official: `https://github.com/YueWu0301/BOPD` (`code_status: released`).
- Paper: LoRA rank 64, $\alpha=128$, LR $5\times 10^{-6}$, clip $\tau=0.05$, 1024-token student rollouts.

## Quickstart Implementation

```python
from __future__ import annotations

def bopd_stages(initial, opsd_train, opd_train):
    teacher = opsd_train(student=initial.copy(), privileged=True)
    return opd_train(student=initial.copy(), teacher=teacher, privileged=False)
```

Do not retarget locked SOTA from this recipe.
