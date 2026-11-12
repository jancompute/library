---
id: recipe:hilo-lora-sync
type: recipe
title: 'HiLo (LoRA Sync)'
method: method:hilo-lora-sync
task: task:frontier-rl-posttrain-stack
target_hardware: 'Paper: Qwen3-1.7B / 0.6B rank-64 LoRA, bandwidth-limited learner-to-worker unicast'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- hilo-lora-sync
---

# HiLo (LoRA Sync)

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-12. Workers replicate LoRA parameters and optimizer state. Distinct from `method:hilo-rd`.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def hilo_step(
    residual: torch.Tensor,
    grad: torch.Tensor,
    encode,
    decode,
    optimizer,
) -> tuple[torch.Tensor, object]:
    corrected = grad + residual
    payload = encode(corrected)
    decoded = decode(payload)
    residual = corrected - decoded
    optimizer.zero_grad(set_to_none=True)
    for p in optimizer.param_groups[0]["params"]:
        p.grad = decoded
        break
    optimizer.step()
    return residual, payload
```

Do not retarget locked SOTA from this recipe.
