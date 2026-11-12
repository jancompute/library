---
id: recipe:autoscaffold
type: recipe
title: AutoScaffold
method: method:autoscaffold
task: task:math-code-rl-dense
target_hardware: 'Paper: Qwen3-4B-Instruct math GRPO/DAPO; ALFWorld and search QA on GiGPO'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- autoscaffold
---

# AutoScaffold

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-12. Overlay on GRPO/DAPO/GiGPO. Cap class-level injection $q[C]\le q_{\max}<1$. Validate class edits on held-out tasks before the next block.

## Quickstart Implementation

```python
from __future__ import annotations

from typing import Mapping


def scaffolded_prompt(
    task: str,
    class_id: str,
    class_scaffold: Mapping[str, str],
    inst_scaffold: Mapping[str, str],
    inject_class: bool,
) -> str:
    parts = [task]
    if inject_class and class_scaffold.get(class_id):
        parts.append(class_scaffold[class_id])
    if inst_scaffold.get(task):
        parts.append(inst_scaffold[task])
    return "\n".join(parts)
```

Do not retarget locked SOTA from this recipe.
