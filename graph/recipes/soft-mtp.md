---
id: recipe:soft-mtp
type: recipe
title: 'Soft-MTP'
method: method:soft-mtp
task: task:diffusion-augmented-ar
target_hardware: 'Paper: MTP pretrain / speculative decode heads'
framework: PyTorch
repo_url: https://github.com/JaydenTeoh/Soft-MTP
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- soft-mtp
---

# Soft-MTP

## Hardware & Environment Setup
- Official: `https://github.com/JaydenTeoh/Soft-MTP`.
- `code_status: released` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def soft_mtp_loss(ntp_ce, mtp_ce):
    # recover KL(mtp || ntp) from two CE grads; drop the noisy residual
    return ntp_ce.detach() + (mtp_ce - ntp_ce)
```

Do not retarget locked SOTA from this recipe.
