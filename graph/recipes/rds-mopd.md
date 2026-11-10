---
id: recipe:rds-mopd
type: recipe
title: 'RDS-MOPD'
method: method:rds-mopd
task: task:student-distillation
target_hardware: 'Paper: SmolLM3-3B Open-MOPD host, 150 steps'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- rds-mopd
---

# RDS-MOPD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-10. Host is the Open-MOPD trainer.

## Quickstart Implementation

```python
from __future__ import annotations

import math

def rds_nominal(clipped_kl, noise_floor, eps=1e-6):
    temp = max(noise_floor, eps)
    logits = [-m / temp for m in clipped_kl]
    m = max(logits)
    exps = [math.exp(x - m) for x in logits]
    z = sum(exps)
    return [e / z for e in exps]
```

Do not retarget locked SOTA from this recipe.
