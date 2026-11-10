---
id: recipe:care-po
type: recipe
title: 'CARE-PO'
method: method:care-po
task: task:outcome-only-long-horizon-agent-rl
target_hardware: 'Paper: GAIA GRPO host'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- care-po
---

# CARE-PO

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-10.

## Quickstart Implementation

```python
from __future__ import annotations

def care_po_efficiency_adv(n_calls: float, n_ref: float) -> float:
    return (n_ref - n_calls) / max(n_ref, 1.0)
```

Do not retarget locked SOTA from this recipe.
