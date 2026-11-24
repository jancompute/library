---
id: recipe:aprm
type: recipe
title: APRM
method: method:aprm
task: task:math-code-rl-dense
target_hardware: 'Paper: Qwen3-1.7B/4B-Base GRPO/GPG; Qwen3.5-2B DAPO'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- aprm
---

# APRM

## Hardware & Environment Setup
- `code_status: none` as of 2026-11-24. No public GitHub. Mix a ~46M attention process RM into group advantages at \(\beta=0.3\). Does not replace CISPO.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def mix_process(outcome: torch.Tensor, process: torch.Tensor, beta: float = 0.3) -> torch.Tensor:
    return (1.0 - beta) * outcome + beta * process
```
