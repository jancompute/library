---
id: recipe:gumbel-substitution
type: recipe
title: Gumbel Substitution
method: method:gumbel-substitution
task: task:fp4-rl-train-rollout-alignment
target_hardware: 'Paper: 2B/9B lab mismatch; Reliquary 9B, 161 sampler accounts'
framework: PyTorch
repo_url: https://github.com/reliquadotai/reliquary
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- gumbel-substitution
---

# Gumbel Substitution

## Hardware & Environment Setup
- Official: `https://github.com/reliquadotai/reliquary`
- `code_status: released` as of 2026-11-23. Public Gumbel; sampler \(y=\arg\max(\ell^q+G)\); trainer scores \(v^*=\arg\max(\ell^p+G)\). Does not replace TRACE / TRIAGE.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def gumbel_token(logits: torch.Tensor, gumbel: torch.Tensor) -> torch.Tensor:
    return torch.argmax(logits + gumbel, dim=-1)
```
