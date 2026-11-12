---
id: recipe:physopsd
type: recipe
title: PhysOPSD
method: method:physopsd
task: task:posttrain-diffusion
target_hardware: 'Paper: UniVideo 13B / OmniWeaving 8.3B video generators'
framework: PyTorch
repo_url: https://github.com/aigc3d/PhysOPSD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- physopsd
---

# PhysOPSD

## Hardware & Environment Setup
- Official: `https://github.com/aigc3d/PhysOPSD` (`code_status: released`).
- Site: `https://haroldchen19.github.io/PhysOPSD-site/`. Compile scene code into teacher-only physical context. Train on PhysOPSD-3K, not an 80K SFT mix.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def physopsd_loss(
    student_logits: torch.Tensor,
    teacher_logits: torch.Tensor,
    token_privilege: torch.Tensor,
) -> torch.Tensor:
    student_logp = F.log_softmax(student_logits, dim=-1)
    teacher_p = F.softmax(teacher_logits, dim=-1)
    kl = (teacher_p * (teacher_p.clamp_min(1e-8).log() - student_logp)).sum(-1)
    return (kl * token_privilege).mean()
```

Do not retarget locked SOTA from this recipe.
