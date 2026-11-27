---
id: method:gated-deltanet-2
type: method
title: "Gated DeltaNet 2"
category: "architecture"
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: "symmetric GDN-2 erase / decay-regulated residual write (Stable GDN-2; not Gated DeltaNet 2 stub)"
    reason: "Gated DeltaNet 2 remains the 2605.22791 stub; Stable GDN-2 is a later erase/write rewrite"
    use_instead: method:stable-gdn-2
last_reviewed: '2026-11-27'
papers:
  - paper:stable-gdn-2
  - paper:gated-deltanet-2
recipes:
  - recipe:gated-deltanet-2
claims:
  - benchmark: "Long-Sequence Associative Recall"
    metric: "recall accuracy & throughput"
    value: "Closes gap with full attention at O(N) training compute"
    baseline: "Mamba-2 / DeltaNet"
    date: "2026-08-26"
    verified: true
    notes: "Dynamic associative delta memory updates with hardware-efficient chunkwise formulation."
tags:
  - architecture
  - linear-attention
  - recurrent
  - gated-deltanet
---

# Gated DeltaNet 2

## Method Overview
Gated DeltaNet 2 incorporates an enhanced dynamic delta memory rule into linear recurrent networks, updating associative memory matrices via fast chunkwise matrix multiplications on GPU tensor cores.

## When to Use
- Ultra-long context sequence processing with linear training complexity and constant generation memory.
