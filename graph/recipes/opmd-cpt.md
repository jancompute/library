---
id: recipe:opmd-cpt
type: recipe
title: 'OPMD-CPT'
method: method:opmd-cpt
task: task:student-distillation
target_hardware: 'Paper: Qwen3-1.7B-Base student, Qwen3-4B/14B teacher, 1B MegaMath tokens'
framework: PyTorch
repo_url: https://github.com/ShuidiH20/OPMD
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- opmd-cpt
---

# OPMD-CPT

## Hardware & Environment Setup
- Official: `https://github.com/ShuidiH20/OPMD` (`code_status: announced`; 404 as of 2026-11-11).
- Distinct from `recipe:opmd` (post-train mechanism OPD). Proxy for anchors: DeepSeek-R1-Distill-Qwen-1.5B entropy scan, window 4096 / stride 2048.

## Quickstart Implementation

```python
from __future__ import annotations

import torch.nn.functional as F


def opmd_cpt_token_loss(student_logp, teacher_logp):
    return F.kl_div(student_logp, teacher_logp.exp(), reduction="batchmean", log_target=False)
```

Do not retarget locked SOTA from this recipe.
