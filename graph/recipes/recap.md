---
id: recipe:recap
type: recipe
title: RECAP
method: method:recap
task: task:long-horizon-tool-agent
target_hardware: 'Paper: Qwen3.5-4B VeRL async GRPO, group 8, 150 steps'
framework: PyTorch / VeRL
repo_url: https://github.com/eth-medical-ai-lab/recap
code_status: released
pip_dependencies:
- torch>=2.5.0
- verl
tags:
- recipe
- recap
---

# RECAP

## Hardware & Environment Setup
- Official: `https://github.com/eth-medical-ai-lab/recap`
- `code_status: released` as of 2026-11-25. 32K working context, up to three compaction events, \(\lambda=0.1\) BrowseComp-Plus / \(0.03\) SWE. Does not replace FoldGRPO, RLM, or CANOPY.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def behavior_distortion(
    compact_logits: torch.Tensor,
    full_logits: torch.Tensor,
    action_mask: torch.Tensor,
) -> torch.Tensor:
    log_p = F.log_softmax(compact_logits, dim=-1)
    log_q = F.log_softmax(full_logits.detach(), dim=-1)
    kl = (log_p.exp() * (log_p - log_q)).sum(dim=-1)
    return (kl * action_mask).sum() / action_mask.sum().clamp_min(1)
```
