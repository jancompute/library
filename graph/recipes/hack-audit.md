---
id: recipe:hack-audit
type: recipe
title: 'Hack-Audit (LB)'
method: method:hack-audit
task: task:math-code-rl-dense
target_hardware: 'Paper: budgeted GRPO strong-verifier audits'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- hack-audit
---

# Hack-Audit (LB)

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-10-27.

## Quickstart Implementation

```python
from __future__ import annotations

def audit_order(pass_counts: list[int]) -> list[int]:
    return sorted(range(len(pass_counts)), key=lambda i: pass_counts[i])
```

Do not retarget locked SOTA from this recipe.
