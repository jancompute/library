---
id: method:turnwise
type: method
title: 'TurnWise'
category: multimodal-rl
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:rl-video-mllm'
  reason: 'OraRL remains annotation-as-rollout; TurnWise is turn-level GRPO for streaming video'
  use_instead: method:orarl
assumptions:
- 'Streaming video with an explicit wait/silence action. Sibling of OraRL / FrameGRPO / MPO. Paper header lists Code Model Dataset; no URL as of 2026-11-05.'
last_reviewed: '2026-11-05'
papers:
- paper:turnwise
recipes:
- recipe:turnwise
claims:
- benchmark: 'ProactiveVQA / OVO-Timing / StreamingBench, Qwen2.5-VL-3B and Qwen3-VL-4B'
  metric: 'PAUC / Timing F1 / StreamingBench average'
  value: '3B 43.56 / 21.59 / 49.43 (+3.96 / +3.87 / +0.69); 4B 42.44 / 11.15 / 58.96 (+6.26 / +1.92 / +2.38)'
  baseline: 'strongest non-TurnWise GRPO/SFT streaming baseline per backbone'
  date: '2026-11-05'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.06728'
  notes: 'Turn-mean + remaining-return cuts 3B repetition 15.53→5.98 (−61.5%). Does not retarget method:orarl.'
tags:
- video-mllm
- streaming
- turn-credit
- active
---

# TurnWise

## Method Overview
TurnWise is turn-level GRPO for streaming video. Silence-completed prefix scoring converts a trajectory reward into each decision's remaining return, so later turns are not credited for earlier successes. Turn-mean loss averages tokens inside a turn, then averages turns, so wait actions are not drowned by long replies.

## When to Use
- Streaming video interaction (respond vs wait) where trajectory-level GRPO reinforces redundant replies.

## When NOT to Use
OraRL remains annotation-as-rollout perception RL. FrameGRPO is multi-frame complementary sets, not streaming wait/respond. MPO is text-agent turn-scale advantage.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:rl-video-mllm`. Does **not** replace `method:orarl`. Sibling of `method:framegrpo` and `method:mpo`.

## Gotchas & Failure Modes
- Needs an explicit silence/wait action so prefixes can be scored with remaining turns muted.
- Code announced in the paper header; no URL found as of 2026-11-05.
