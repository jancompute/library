---
id: recipe:automaster
type: recipe
title: AutoMaster
method: method:automaster
task: task:student-distillation
target_hardware: 'Paper: Qwen3.5-4B/9B SFT, 512 traj, 3 epochs'
framework: PyTorch
repo_url: https://github.com/RUCAIBox/AutoMaster
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- automaster
---

# AutoMaster

## Hardware & Environment Setup
- Official: `https://github.com/RUCAIBox/AutoMaster`
- `code_status: released` as of 2026-11-20. Skill-conditioned teacher traces then ordinary SFT. Does not replace OPD.

## Quickstart Implementation

```python
from __future__ import annotations


def keep_skill_trace(trace: str, skills: list[str]) -> bool:
    lowered = trace.lower()
    return any(skill.lower() in lowered for skill in skills)
```
