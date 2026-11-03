---
id: recipe:oc-opd
type: recipe
title: 'OC-OPD'
method: method:oc-opd
task: task:student-distillation
target_hardware: 'Paper: non-thinking / thinking / base-init students'
framework: PyTorch
repo_url: https://github.com/RuoranXu/OC-OPD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- oc-opd
---

# OC-OPD

## Hardware & Environment Setup
- Official: `https://github.com/RuoranXu/OC-OPD`.
- `code_status: released` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def oc_bargain(rev_grad, fwd_grad, scale):
    return scale * (rev_grad + fwd_grad) / 2
```

Do not retarget locked SOTA from this recipe.
