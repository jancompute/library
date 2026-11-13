---
id: recipe:hive-mem
type: recipe
title: HiVe-Mem
method: method:hive-mem
task: task:agent-memory
target_hardware: 'Paper: Qwen3-VL-4B multimodal agent memory'
framework: PyTorch
repo_url: https://github.com/ViktorAxelsen/HiVe-Mem
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- hive-mem
---

# HiVe-Mem

## Hardware & Environment Setup
- Official: `https://github.com/ViktorAxelsen/HiVe-Mem` (`code_status: released`).
- Expand neighbors horizontally, compose evidence vertically, then let the selector choose the view. Distinct from `method:hive-synth`.

## Quickstart Implementation

```python
from __future__ import annotations

from typing import Sequence


def expand_horizontal(hit_ids: Sequence[str], neighbors: dict[str, list[str]], k: int = 4) -> list[str]:
    out: list[str] = []
    seen: set[str] = set()
    for hid in hit_ids:
        for nid in [hid, *neighbors.get(hid, [])][:k]:
            if nid not in seen:
                seen.add(nid)
                out.append(nid)
    return out
```

Do not retarget locked SOTA from this recipe.
