---
id: recipe:gated-loop-moe
type: recipe
title: Gated-Loop MoE
method: method:gated-loop-moe
task: task:compute-matched-moe-looped-pretrain
target_hardware: 'Paper: 69B MLA / 51B KDA at 1T tokens; 200B reproduction'
framework: PyTorch
repo_url: announced
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- gated-loop-moe
---

# Gated-Loop MoE

## Hardware & Environment Setup
- `code_status: announced` as of 2026-11-26. GitHub URL 404. Gated Core plus Prelude-to-Coda residual; extra experts from saved depth. 200B PPL listing is not SMELT Chinchilla protocol. Does not replace SMELT.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn.functional as F


def gated_loop_step(h: torch.Tensor, delta: torch.Tensor, gate_logits: torch.Tensor) -> torch.Tensor:
    gate = torch.sigmoid(gate_logits)
    return h + gate * delta


def prelude_to_coda(prelude: torch.Tensor, coda: torch.Tensor) -> torch.Tensor:
    return coda + F.rms_norm(prelude, (prelude.shape[-1],))
```
