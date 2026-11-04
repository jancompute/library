---
id: recipe:dory
type: recipe
title: 'Dory'
method: method:dory
task: task:elastic-depth-looped-lm
target_hardware: 'Paper: Dory1.0-4B, 6T tokens (4.5T NVFP4)'
framework: PyTorch
repo_url: https://huggingface.co/collections/nvidia/nemotron-labs-dory
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- dory
---

# Dory

## Hardware & Environment Setup
- Weights: `https://huggingface.co/collections/nvidia/nemotron-labs-dory`.
- Official train code: `none found` (`code_status: none`) as of 2026-11-04.

## Quickstart Implementation

```python
from __future__ import annotations

def dory_loop_count(difficulty, k_max):
    return min(k_max, 1 + int(difficulty))
```

Do not retarget locked SOTA from this recipe.
