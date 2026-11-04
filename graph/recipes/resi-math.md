---
id: recipe:resi-math
type: recipe
title: 'ReSI-Math'
method: method:resi-math
task: task:math-code-rl-dense
target_hardware: 'Paper: Qwen3-VL-8B one-shot RLVR stages'
framework: PyTorch
repo_url: https://github.com/CNU-Bot-Group/ReSI-Math
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- resi-math
---

# ReSI-Math

## Hardware & Environment Setup
- Official: `https://github.com/CNU-Bot-Group/ReSI-Math`.
- `code_status: released` as of 2026-11-04.

## Quickstart Implementation

```python
from __future__ import annotations

def resi_recoverable(pre, post, threshold):
    return (pre < threshold) and (post >= threshold)
```

Do not retarget locked SOTA from this recipe.
