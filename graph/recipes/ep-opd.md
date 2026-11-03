---
id: recipe:ep-opd
type: recipe
title: 'EP-OPD'
method: method:ep-opd
task: task:student-distillation
target_hardware: 'Paper: Qwen3-4B QASPER / PeerQA'
framework: PyTorch
repo_url: https://github.com/RuoranXu/EP-OPD
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- ep-opd
---

# EP-OPD

## Hardware & Environment Setup
- Official: `https://github.com/RuoranXu/EP-OPD`.
- `code_status: released` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def ep_margin(logp_supported, logp_alt):
    return (logp_supported - logp_alt).clamp_min(0)
```

Do not retarget locked SOTA from this recipe.
