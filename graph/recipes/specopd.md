---
id: recipe:specopd
type: recipe
title: 'SpecOPD'
method: method:specopd
task: task:diffusion-augmented-ar
target_hardware: 'Paper: 8B / 27B / 125B speculative drafters'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- specopd
---

# SpecOPD

## Hardware & Environment Setup
- Official: `none found`.
- Related Draft-OPD: `https://github.com/Simplified-Reasoning/Draft-OPD`.
- `code_status: none` as of 2026-11-05.

## Quickstart Implementation

```python
from __future__ import annotations

def specopd_branch(anchor_prefix, draft_tokens):
    return (*anchor_prefix, *draft_tokens)
```

Do not retarget locked SOTA from this recipe.
