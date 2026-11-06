---
id: recipe:stage-lora
type: recipe
title: 'Stage-LoRA'
method: method:stage-lora
task: task:lora-quality-tuning
target_hardware: 'Paper: Llama-3.2-1B/3B LoRA on GSM8K SFT and GRPO'
framework: PyTorch
repo_url: none found
code_status: none
pip_dependencies:
- torch>=2.5.0
tags:
- recipe
- stage-lora
---

# Stage-LoRA

## Hardware & Environment Setup
- Official: `none found`.
- `code_status: none` as of 2026-11-06.

## Quickstart Implementation

```python
from __future__ import annotations

def stage_lora_rl_b(B, dB, flatten):
    gram = B.T @ B
    P = B @ gram.pinverse() @ B.T
    return P @ dB + flatten((dB - P @ dB))
```

Do not retarget locked SOTA from this recipe.
