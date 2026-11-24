---
id: recipe:saepo
type: recipe
title: SAEPO
method: method:saepo
task: task:math-code-rl-dense
target_hardware: 'Paper: Qwen3-1.7B/4B-Base GRPO/GSPO; OLMo-3-7B-Base'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- saepo
---

# SAEPO

## Hardware & Environment Setup
- `code_status: none` as of 2026-11-24. No public GitHub. Frozen SAE contrast of correct vs incorrect group tokens. Does not replace CISPO.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def sae_credit(token_feat: torch.Tensor, correct_mean: torch.Tensor, incorrect_mean: torch.Tensor) -> torch.Tensor:
    pos = torch.nn.functional.cosine_similarity(token_feat, correct_mean, dim=-1)
    neg = torch.nn.functional.cosine_similarity(token_feat, incorrect_mean, dim=-1)
    return pos - neg
```
