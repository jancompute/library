---
id: recipe:rollout-reuse
type: recipe
title: Rollout Reuse
method: method:rollout-reuse
task: task:student-distillation
target_hardware: 'Paper: Qwen3-4B/8B teacher GRPO on 8xL40S; multi-family students'
framework: PyTorch
repo_url: https://github.com/vashistht/rollout_reuse
code_status: released
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- rollout-reuse
---

# Rollout Reuse

## Hardware & Environment Setup
- Official: `https://github.com/vashistht/rollout_reuse`
- `code_status: released` as of 2026-11-23. Pass-rate ordered SFT then mixed-success DPO on saved teacher GRPO traces. Does not replace OPD.

## Quickstart Implementation

```python
from __future__ import annotations


def order_by_pass_rate(prompts: list[str], pass_rate: dict[str, float]) -> list[str]:
    return sorted(prompts, key=lambda x: pass_rate[x])


def teacher_top1(completions: list[str], teacher_logp: list[float]) -> str:
    return completions[max(range(len(completions)), key=lambda i: teacher_logp[i])]
```
