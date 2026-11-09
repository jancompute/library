---
id: recipe:fprt
type: recipe
title: 'FPRT'
method: method:fprt
task: task:student-distillation
target_hardware: 'Paper: Llama-3.1-8B / DeepSeek-Math-7B SFT on 88.90K traces'
framework: PyTorch
repo_url: https://github.com/visresearch/FPRT
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- fprt
---

# FPRT

## Hardware & Environment Setup
- Official: `https://github.com/visresearch/FPRT`.
- `code_status: released` as of 2026-11-09.

## Quickstart Implementation

```python
from __future__ import annotations

def fprt_mode(k_wrong, unique_wrong):
    if unique_wrong == 1:
        return "stubborn"
    if unique_wrong >= k_wrong:
        return "inconsistent"
    return "sporadic"
```

Do not retarget locked SOTA from this recipe.
