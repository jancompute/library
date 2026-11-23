---
id: recipe:creditfilter
type: recipe
title: CreditFilter
method: method:creditfilter
task: task:math-code-rl-dense
target_hardware: 'Paper: Qwen3-8B-Base DAPO-17k, 128 prompts x 16 responses'
framework: PyTorch
repo_url: https://github.com/yoctta/CreditFilter
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- creditfilter
---

# CreditFilter

## Hardware & Environment Setup
- Official: `https://github.com/yoctta/CreditFilter` (verl overlay, Apache-2.0)
- `code_status: released` as of 2026-11-23. Exponential window over within-response entropy rank on a DAPO host. Does not replace CISPO.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def creditfilter_weights(entropy: torch.Tensor, width: float) -> torch.Tensor:
    rank = torch.argsort(torch.argsort(entropy, descending=True))
    return torch.exp(-rank.float() / width)
```
