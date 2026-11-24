---
id: recipe:recurrent-student-opd
type: recipe
title: Recurrent Student OPD
method: method:recurrent-student-opd
task: task:student-distillation
target_hardware: 'Paper: 0.4B from-scratch / Qwen2.5-0.5B + 3B/7B teachers'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- recurrent-student-opd
---

# Recurrent Student OPD

## Hardware & Environment Setup
- `code_status: none` as of 2026-11-24. No public GitHub. Convert the student to cross-token recurrence during OPD (~+3% params, \(1.1\times\) decode). Does not replace OPD or ELR.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn as nn


class FeedbackMix(nn.Module):
    def __init__(self, hidden: int):
        super().__init__()
        self.proj = nn.Linear(hidden, hidden, bias=False)
        nn.init.zeros_(self.proj.weight)

    def forward(self, hidden: torch.Tensor, prev: torch.Tensor | None) -> torch.Tensor:
        if prev is None:
            return hidden
        return hidden + self.proj(prev)
```
