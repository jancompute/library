---
id: recipe:memento
type: recipe
title: 'MEMENTO'
method: method:memento
task: task:long-context-prompt-offload
target_hardware: 'Paper: Qwen3-8B, books to 2.5M tokens, 20K window'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- memento
---

# MEMENTO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def memento_reward(answer_ok, note_quality, conf_cal):
    return float(answer_ok) + note_quality + conf_cal
```

Do not retarget locked SOTA from this recipe.
