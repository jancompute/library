---
id: recipe:deletion-tuning
type: recipe
title: 'Deletion Tuning'
method: method:deletion-tuning
task: task:lora-quality-tuning
target_hardware: 'Paper: Llama-3-8B / Qwen2.5-7B GRPO, <0.05% gate-projection zeros'
framework: PyTorch
repo_url: https://github.com/agentic-learning-ai-lab/deleting-weights
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- deletion-tuning
---

# Deletion Tuning

## Hardware & Environment Setup
- Official: `https://github.com/agentic-learning-ai-lab/deleting-weights` (`code_status: released`).
- Hugging Face Daily leftover 2026-11-10. Default $\eta=1/2048$, $\lambda=10^{-5}$, $\mathit{lr}=3\times 10^{-4}$. Mask only the SwiGLU gate projection.

## Quickstart Implementation

```python
from __future__ import annotations

import torch
import torch.nn as nn


class DeletionGate(nn.Module):
    def __init__(self, weight: torch.Tensor):
        super().__init__()
        self.weight = weight
        self.logits = nn.Parameter(torch.zeros_like(weight))

    def forward(self, alpha: float) -> torch.Tensor:
        return self.weight * torch.sigmoid(alpha * self.logits)
```

Do not retarget locked SOTA from this recipe.
