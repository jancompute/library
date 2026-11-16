---
id: recipe:concertina
type: recipe
title: Concertina
method: method:concertina
task: task:student-distillation
target_hardware: 'Paper: Qwen3-4B folded N=2 to 2.27B on 22B tokens'
framework: PyTorch
repo_url: https://github.com/myboker/concertina
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- concertina
---

# Concertina

## Hardware & Environment Setup
- Official: `https://github.com/myboker/concertina` (`code_status: released`).
- Fold every N adjacent teacher layers into one shared block executed N times. Mix 35% math / 55% knowledge / 10% web. FKL+CE, not reverse-KL OPD.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def concertina_fkl_ce(student_logits: torch.Tensor, teacher_logits: torch.Tensor, labels: torch.Tensor) -> torch.Tensor:
    fkl = F.kl_div(
        F.log_softmax(student_logits, dim=-1),
        F.softmax(teacher_logits, dim=-1),
        reduction="batchmean",
    )
    ce = F.cross_entropy(student_logits.reshape(-1, student_logits.size(-1)), labels.reshape(-1))
    return fkl + ce
```

Do not retarget locked SOTA from this recipe.
