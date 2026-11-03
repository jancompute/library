---
id: recipe:sonar-moe
type: recipe
title: 'Sonar-MoE'
method: method:sonar-moe
task: task:full-param-memory-efficient-pretrain
target_hardware: 'Paper: OLMoE-1B-7B / Granite-3.1-3B-A800M bf16'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- sonar-moe
---

# Sonar-MoE

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def sonar_expert_backward(expert, grad, opt):
    opt.update(expert, grad)
    return None
```

Do not retarget locked SOTA from this recipe.
