---
id: recipe:sepo
type: recipe
title: 'SEPO'
method: method:sepo
task: task:math-code-rl-dense
target_hardware: 'Paper: self-evolution RLVR'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- sepo
---

# SEPO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def elicit(prompt: str, label: str) -> str:
    return prompt + '\nHint: ' + label
```

Do not retarget locked SOTA from this recipe.
