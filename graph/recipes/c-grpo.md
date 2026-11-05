---
id: recipe:c-grpo
type: recipe
title: 'C-GRPO'
method: method:c-grpo
task: task:math-code-rl-dense
target_hardware: 'Paper: Qwen2.5-7B-Instruct / Llama-3.1-8B GRPO'
framework: PyTorch
repo_url: https://github.com/AryaFayyazi/CGRPO
code_status: released
pip_dependencies:
- torch>=2.5.0
- trl-cgrpo
tags:
- recipe
- c-grpo
---

# C-GRPO

## Hardware & Environment Setup
- Official: `https://github.com/AryaFayyazi/CGRPO`.
- TRL subclass: `pip install trl-cgrpo`.
- `code_status: released` as of 2026-11-05.

## Quickstart Implementation

```python
from __future__ import annotations

def cgrpo_stop(pred_set, k, k_max):
    if len(pred_set) == 1:
        return k
    return min(k_max, 2 * k)
```

Do not retarget locked SOTA from this recipe.
