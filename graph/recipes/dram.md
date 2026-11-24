---
id: recipe:dram
type: recipe
title: DRAM
method: method:dram
task: task:full-param-memory-efficient-pretrain
target_hardware: 'Paper: LLaMA 60M–350M C4; Qwen3-8B / LLaMA-3.1-8B / Gemma-2-9B FT'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- dram
---

# DRAM

## Hardware & Environment Setup
- `code_status: none` as of 2026-11-24. No public GitHub. Principal-random subspace Muon with linear rank reallocation \((k-1,1)\to(0,k)\). Does not replace SCALE or Muon2.

## Quickstart Implementation

```python
from __future__ import annotations


def dram_ranks(step: int, total: int, k: int) -> tuple[int, int]:
    frac = min(max(step / max(total, 1), 0.0), 1.0)
    random_rank = max(1, round(1.0 + frac * (k - 1)))
    principal_rank = max(0, k - random_rank)
    return principal_rank, random_rank
```
