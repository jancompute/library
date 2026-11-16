---
id: recipe:sebo
type: recipe
title: SEBO
method: method:sebo
task: task:diffusion-lm-ar-delta-recycle
target_hardware: 'Paper: LLaDA-8B-Instruct masked dLLM post-train'
framework: PyTorch
repo_url: https://github.com/githubhyz/See_Every_Block_Once
code_status: announced
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- sebo
---

# SEBO

## Hardware & Environment Setup
- Official: `https://github.com/githubhyz/See_Every_Block_Once` (`code_status: announced`; empty as of 2026-11-16).
- Estimate the MDLM ELBO by evaluating every denoising block once. Do not sample a random subset of blocks.

## Quickstart Implementation

```python
from __future__ import annotations

from typing import Callable

import torch


def sebo_elbo(block_nll: Callable[[int], torch.Tensor], n_blocks: int) -> torch.Tensor:
    terms = [block_nll(i) for i in range(n_blocks)]
    return torch.stack(terms).mean()
```

Do not retarget locked SOTA from this recipe.
