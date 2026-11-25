---
id: recipe:cot-proxy
type: recipe
title: CoT-Proxy
method: method:cot-proxy
task: task:student-distillation
target_hardware: 'Paper: Qwen3-4B/32B AppWorld; GPT-5.6 Luna closed teacher'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- cot-proxy
---

# CoT-Proxy

## Hardware & Environment Setup
- `code_status: none` as of 2026-11-25. No public GitHub. Empty think block plus KL replay to the initial student. Does not replace OPD or CANOPY.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def cot_proxy_loss(
    action_logits: torch.Tensor,
    action_ids: torch.Tensor,
    replay_logits: torch.Tensor,
    init_logits: torch.Tensor,
    kl_coef: float = 0.1,
) -> torch.Tensor:
    sft = F.cross_entropy(action_logits.flatten(0, -2), action_ids.flatten())
    log_p = F.log_softmax(replay_logits, dim=-1)
    log_q = F.log_softmax(init_logits.detach(), dim=-1)
    kl = (log_p.exp() * (log_p - log_q)).sum(dim=-1).mean()
    return sft + kl_coef * kl
```
