---
id: recipe:mpq
type: recipe
title: 'MPQ'
method: method:mpq
task: task:full-lowbit-finetune
target_hardware: 'Paper: LLM PTQ'
framework: PyTorch
repo_url: https://github.com/poseidonchan/MPQ
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- mpq
---

# MPQ

## Hardware & Environment Setup
- Official: `https://github.com/poseidonchan/MPQ`.
- `code_status: released` as of 2026-10-26.

## Quickstart Implementation

```python
from __future__ import annotations

def keep_alts(cands, k: int):
    if k <= 0 or not cands:
        raise ValueError('cands')
    return cands[:k]
```

Do not retarget locked SOTA from this recipe.
