---
id: recipe:groupclip
type: recipe
title: 'GroupClip'
method: method:groupclip
task: task:linear-time-sequence-modeling
target_hardware: 'Paper: gated SSM CPT / from-scratch'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- groupclip
---

# GroupClip

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-04.

## Quickstart Implementation

```python
from __future__ import annotations

def groupclip(embed, max_norm):
    return embed.clamp(-max_norm, max_norm)
```

Do not retarget locked SOTA from this recipe.
