---
id: recipe:instructreplay
type: recipe
title: InstructReplay
method: method:instructreplay
task: task:instruct-sft-alignment
target_hardware: 'Paper: three families × two domains, 9,600 frozen M0 assistant turns'
framework: PyTorch
repo_url: https://github.com/xiaofengShi/InstructReplay
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- instructreplay
---

# InstructReplay

## Hardware & Environment Setup
- Official: `https://github.com/xiaofengShi/InstructReplay`
- `code_status: released` as of 2026-11-25. Mix domain NLL with full next-token match on frozen M0 assistant turns. Does not replace OLMo-3 or DCO.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def instruct_replay_loss(
    domain_logits: torch.Tensor,
    domain_labels: torch.Tensor,
    replay_logits: torch.Tensor,
    replay_teacher_logp: torch.Tensor,
    beta: float = 1.0,
) -> torch.Tensor:
    domain = F.cross_entropy(domain_logits.flatten(0, -2), domain_labels.flatten())
    student_logp = F.log_softmax(replay_logits, dim=-1)
    replay = (replay_teacher_logp.exp() * (replay_teacher_logp - student_logp)).sum(dim=-1).mean()
    return domain + beta * replay
```
