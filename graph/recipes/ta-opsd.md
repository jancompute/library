---
id: recipe:ta-opsd
type: recipe
title: TA-OPSD
method: method:ta-opsd
task: task:privileged-teacher-opsd
target_hardware: 'Paper: Qwen3 1.7B/4B/8B privileged OPSD'
framework: PyTorch
repo_url: https://github.com/gtbxdf4/TA-OPSD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- ta-opsd
---

# TA-OPSD

## Hardware & Environment Setup
- Official: `https://github.com/gtbxdf4/TA-OPSD` (`code_status: released`).
- Keep the OPSD reverse-KL term. Add stop/continue matching on EOS versus continue tokens. Unlikelihood on repeated n-grams in failed student traces.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def ta_opsd_aux(student_eos_logit: torch.Tensor, teacher_continue: torch.Tensor, rep_logp: torch.Tensor) -> torch.Tensor:
    stop = F.binary_cross_entropy_with_logits(student_eos_logit, 1.0 - teacher_continue)
    return stop - 0.1 * rep_logp.mean()
```

Do not retarget locked SOTA from this recipe.
