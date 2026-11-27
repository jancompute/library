---
id: method:stable-gdn-2
type: method
title: Stable GDN-2
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:linear-time-sequence-modeling'
  reason: 'Mamba-2 remains the architecture hop; Stable GDN-2 stabilizes GDN-2 erase/write'
  use_instead: method:mamba-2
- when: 'GGA mixed-precision + Pure-Write window for GDN recurrent-state quant'
  reason: 'GGA-PW is GDN state quant; Stable GDN-2 is a full-precision erase/write rewrite'
  use_instead: method:gga-pw
- when: 'periodic 4-bit recurrent-state quantization (PACE)'
  reason: 'PACE is periodic 4-bit SSM state storage; Stable GDN-2 is not a quant recipe'
  use_instead: method:pace
- when: 'original GDN-2 architecture stub (not the 2611.34051 stability rewrite)'
  reason: 'gated-deltanet-2 is the 2605.22791 architecture card; this is the symmetric-erase rewrite'
  use_instead: method:gated-deltanet-2
assumptions:
- 'Host is Gated DeltaNet-2 channel-wise erase/write. Symmetric erase plus decay-regulated residual write. 1.6B recurrent/hybrid 64K pretrain. No public train code as of 2026-11-27.'
last_reviewed: '2026-11-27'
papers:
- paper:stable-gdn-2
recipes:
- recipe:stable-gdn-2
claims:
- benchmark: '1.6B recurrent GDN-2 vs Stable GDN-2 at 64K pretrain'
  metric: 'RULER 128K average'
  value: '+6.80 vs GDN-2'
  baseline: 'GDN-2'
  date: '2026-11-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.34051'
  notes: 'Does not retarget method:mamba-2, method:gga-pw, method:pace, or method:gated-deltanet-2.'
- benchmark: '1.6B hybrid GDN-2 vs Stable GDN-2'
  metric: 'nine-task average accuracy'
  value: '+0.62 vs GDN-2'
  baseline: 'hybrid GDN-2'
  date: '2026-11-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.34051'
  notes: 'Finite-loss runs can still hold state entries >1e36. No public code.'
tags:
- linear-attention
- gated-deltanet
- stability
- active
---

# Stable GDN-2

## Method Overview
Stable GDN-2 keeps GDN-2's independent channel-wise erase and write gates but splits the erase gate symmetrically across the two key factors so reading and modification share a direction. A residual write, amplitude-gated by the forget decay, restores write flexibility without reintroducing expansion. The update stays an input-dependent affine map, so chunkwise parallel kernels still apply.

## When to Use
- Training GDN-2 / hybrid GDN-2 at long context (64K+) when the recurrent state explodes or retrieval collapses even though the loss stays finite.

## When NOT to Use
Architecture first hop remains Mamba-2. GDN state quant remains GGA-PW / PACE. The original GDN-2 architecture card is `method:gated-deltanet-2`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:mamba-2`, `method:gga-pw`, `method:pace`, or `method:gated-deltanet-2`.

## Gotchas & Failure Modes
- Loss-based monitoring misses capacity collapse: finished runs can still hold state entries \(>10^{36}\).
- No public train code as of 2026-11-27.
- GDN-2-specific; not a generic SSM stabilizer.
