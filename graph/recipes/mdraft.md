---
id: recipe:mdraft
type: recipe
title: 'MDraft'
method: method:mdraft
task: task:diffusion-augmented-ar
target_hardware: 'Paper: one-step diffusion drafters'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- mdraft
---

# MDraft

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-30.

## Quickstart Implementation

```python
from __future__ import annotations

def mdraft_target(verifier_probs):
    return sum(verifier_probs) / len(verifier_probs)
```

Do not retarget locked SOTA from this recipe.
