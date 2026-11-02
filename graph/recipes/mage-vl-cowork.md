---
id: recipe:mage-vl-cowork
type: recipe
title: 'Mage-VL-Cowork'
method: method:mage-vl-cowork
task: task:hybrid-computer-use-agent-rl
target_hardware: 'Paper: 4B hybrid CUA'
framework: PyTorch
repo_url: https://github.com/microsoft/Mage
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- mage-vl-cowork
---

# Mage-VL-Cowork

## Hardware & Environment Setup
- Official: `https://github.com/microsoft/Mage`.
- `code_status: released` as of 2026-11-02.

## Quickstart Implementation

```python
from __future__ import annotations

STAGES = ("midtrain", "sft_gui", "sft_code", "sft_hybrid", "rl")

def mage_curriculum(stage):
    return STAGES.index(stage)
```

Do not retarget locked SOTA from this recipe.
