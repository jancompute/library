---
id: recipe:moeresq
type: recipe
title: 'MoeResQ'
method: method:moeresq
task: task:fp4-rl-train-rollout-alignment
target_hardware: 'Paper: Qwen3-30B-A3B GRPO, VeRL+vLLM+FSDP'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- moeresq
---

# MoeResQ

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-04.

## Quickstart Implementation

```python
from __future__ import annotations

def moeresq_corrected(fp4_out, residual):
    return fp4_out + residual
```

Do not retarget locked SOTA from this recipe.
