---
id: recipe:sftprobe
type: recipe
title: 'SFTProbe'
method: method:sftprobe
task: task:instruct-sft-alignment
target_hardware: 'Paper: reasoning SFT data probe'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- sftprobe
---

# SFTProbe

## Hardware & Environment Setup
- Official: `none found`.
- Project: `https://bigml-cs-ucla.github.io/SFTProbe-page/`.
- `code_status: none` as of 2026-11-03.

## Quickstart Implementation

```python
from __future__ import annotations

def probe_loss(losses, keep=0.05):
    n = max(1, int(len(losses) * keep))
    return sum(losses[:n]) / n
```

Do not retarget locked SOTA from this recipe.
