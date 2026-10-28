---
id: recipe:guided-rlvr
type: recipe
title: 'Guided-RLVR'
method: method:guided-rlvr
task: task:math-code-rl-dense
target_hardware: 'Paper: math/code RLVR'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- guided-rlvr
---

# Guided-RLVR

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-28.

## Quickstart Implementation

```python
from __future__ import annotations

def inject_steering(logits, token_id, boost=2.0):
    logits = logits.clone()
    logits[token_id] = logits[token_id] + boost
    return logits
```

Do not retarget locked SOTA from this recipe.
