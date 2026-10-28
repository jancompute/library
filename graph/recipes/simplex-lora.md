---
id: recipe:simplex-lora
type: recipe
title: 'SimplexLoRA'
method: method:simplex-lora
task: task:lora-quality-tuning
target_hardware: 'Paper: Llama 3.1 8B / Qwen3-8B LoRA'
framework: PyTorch
repo_url: https://github.com/brain-lab-research/SimplexLoRA
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- simplex-lora
---

# SimplexLoRA

## Hardware & Environment Setup
- Official: `https://github.com/brain-lab-research/SimplexLoRA`.
- `code_status: released` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def simplex_project(weights, n):
    s = sum(max(w, 0.0) for w in weights) + 1e-12
    return [n * max(w, 0.0) / s for w in weights]
```

Do not retarget locked SOTA from this recipe.
