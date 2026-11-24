---
id: recipe:muted-distillation
type: recipe
title: Muted Distillation
method: method:muted-distillation
task: task:student-distillation
target_hardware: 'Paper: Qwen3.5 4B/9B/27B, OfficeQA Pro / SpreadsheetBench'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- muted-distillation
---

# Muted Distillation

## Hardware & Environment Setup
- `code_status: none` as of 2026-11-24. No public GitHub. Hide student thoughts from the teacher; reverse-KL on the visible tail. Does not replace OPD.

## Quickstart Implementation

```python
from __future__ import annotations

EMPTY_THOUGHT = "<think>\n\n</think>\n"


def mute_teacher_prefix(visible_prefix: str) -> str:
    return visible_prefix + EMPTY_THOUGHT
```
