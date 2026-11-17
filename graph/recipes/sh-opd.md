---
id: recipe:sh-opd
type: recipe
title: SH-OPD
method: method:sh-opd
task: task:student-distillation
target_hardware: 'Paper: math/code OPD with a shared batch horizon'
framework: PyTorch
repo_url: https://github.com/chen123CtrlS/SH-OPD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- sh-opd
---

# SH-OPD

## Hardware & Environment Setup
- Official: `https://github.com/chen123CtrlS/SH-OPD` (`code_status: released`).
- Sample one horizon per batch. Truncate student and teacher sequences to that horizon. Do not schedule per sequence (that is Flash-OPD).

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def sh_opd_horizon(min_h: int, max_h: int, generator: torch.Generator | None = None) -> int:
    return int(torch.randint(min_h, max_h + 1, (1,), generator=generator).item())
```

Do not retarget locked SOTA from this recipe.
