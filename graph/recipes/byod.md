---
id: recipe:byod
type: recipe
title: 'BYOD'
method: method:byod
task: task:diffusion-lm-ar-delta-recycle
target_hardware: 'Paper: one Colab GPU, 3.1-4.0h per 7B-9B conversion'
framework: PyTorch
repo_url: https://github.com/RuurdKuiper/BYOD
code_status: released
pip_dependencies:
- torch>=2.5.0
- peft
tags:
- recipe
- byod
---

# BYOD

## Hardware & Environment Setup
- Official: `https://github.com/RuurdKuiper/BYOD`.
- `code_status: released` as of 2026-11-02.

## Quickstart Implementation

```python
from __future__ import annotations

def byod_trainable(name, param):
    return "lora_" in name and param.requires_grad
```

Do not retarget locked SOTA from this recipe.
