---
id: recipe:flashmorph2
type: recipe
title: FlashMorph2
method: method:flashmorph2
task: task:posttrain-attention-sparsification
target_hardware: 'Paper: Qwen3 0.6B–8B layer selection in 0.72–3.57 GPU-h'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- flashmorph2
---

# FlashMorph2

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-19 (v1 is LanDisen/FlashMorph). Sample discrete hybrid masks, run end-to-end on self-generated hidden states, jointly train selection scores and recovery weights.

## Quickstart Implementation

```python
from __future__ import annotations

import torch


def hybrid_mask(scores: torch.Tensor, k: int) -> torch.Tensor:
    idx = torch.topk(scores, k).indices
    mask = torch.zeros_like(scores)
    mask[idx] = 1.0
    return mask
```

Do not retarget locked SOTA from this recipe.
