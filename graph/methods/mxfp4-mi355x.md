---
id: method:mxfp4-mi355x
type: method
title: "MXFP4 (Microscaling FP4 Training)"
category: "quantization"
status: sota
sota_for:
  - task:fp4-hardware-training
do_not_use_for:
  - when: "MXFP4 MoE LLM train recipe that closes the gap to BF16 (ALTO)"
    reason: "Quartet-II / MXFP4 remain native FP4 hardware SOTA; ALTO is a GPT-OSS-20B MXFP4 recipe on MLPerf Small MoE"
    use_instead: "method:alto-mxfp4"
  - when: "MXFP4 MoE LLM train recipe that closes the gap to BF16 (ALTO)"
    reason: "MXFP4 remains the format co-default; ALTO is a GPT-OSS-20B recipe"
    use_instead: "method:alto-mxfp4"
papers:
  - paper:mxfp4-mi355x
recipes:
  - recipe:mxfp4-mi355x
claims:
  - benchmark: "Microscaled FP4 Benchmark"
    metric: "numerical stability & hardware utilization"
    value: "Co-default microscaling FP4 hardware training format"
    baseline: "FP8"
    date: "2026-08-26"
    verified: true
    notes: "OCP Microscaling FP4 format specifications for modern accelerators."
tags:
  - quantization
  - fp4
  - mxfp4
  - hardware-training
  - sota
---

# MXFP4 (Microscaling FP4 Training)

## Method Overview
MXFP4 implements the OCP Microscaling FP4 format for high-throughput hardware training, sharing block-level exponents across 32 elements to prevent underflow.

## When to Use
- Microscaled FP4 hardware training across multi-vendor accelerator hardware (e.g. AMD MI355X).
