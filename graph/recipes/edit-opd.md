---
id: recipe:edit-opd
type: recipe
title: 'Edit-OPD'
method: method:edit-opd
task: task:student-distillation
target_hardware: 'Paper: VLM visual mathematical reasoning'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- edit-opd
---

# Edit-OPD

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def edit_span(src: str, dst: str) -> str:
    if src is None or dst is None:
        raise ValueError('span')
    return dst if src != dst else src
```

Do not retarget locked SOTA from this recipe.
