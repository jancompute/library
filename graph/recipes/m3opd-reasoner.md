---
id: recipe:m3opd-reasoner
type: recipe
title: M3OPD-Reasoner
method: method:m3opd-reasoner
task: task:student-distillation
target_hardware: 'Paper: Qwen3.5-9B VLM GSPO teachers then MOPD then MixRL'
framework: PyTorch
repo_url: https://github.com/ngquangtrung57/M3OPD-Reasoner
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- m3opd-reasoner
---

# M3OPD-Reasoner

## Hardware & Environment Setup
- Official: `https://github.com/ngquangtrung57/M3OPD-Reasoner` (`code_status: released`).
- Stage 1: one GSPO teacher per domain. Stage 2: top-32 reverse-KL MOPD. Stage 3: MixRL on the same 193K prompts. Paper MOPD is not the library 83.4% bake-off.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def m3opd_topk_rkl(student_logits: torch.Tensor, teacher_logits: torch.Tensor, k: int = 32) -> torch.Tensor:
    t_logp = F.log_softmax(teacher_logits, dim=-1)
    s_logp = F.log_softmax(student_logits, dim=-1)
    _, idx = torch.topk(t_logp, k, dim=-1)
    t = torch.gather(t_logp, -1, idx)
    s = torch.gather(s_logp, -1, idx)
    return torch.sum(t.exp() * (t - s), dim=-1).mean()
```

Do not retarget locked SOTA from this recipe.
