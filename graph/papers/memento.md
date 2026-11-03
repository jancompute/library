---
id: paper:memento
type: paper
title: 'MEMENTO: Learning Context Management for Long Context Processing Agents'
authors:
- 'Yunfan Zhang'
- 'Taehoon Hwang'
- 'Kathleen McKeown'
- 'Smaranda Muresan'
year: 2026
month: 11
arxiv_id: '2611.00244'
url: https://arxiv.org/abs/2611.00244
methods:
- method:memento
cites:
- paper:rlm
- paper:tacm
tags:
- long-context
- compaction
- active
---

# MEMENTO: Learning Context Management for Long Context Processing Agents

## Abstract Summary
LLM agents over long inputs must decide what to retain in a fixed window. Off-the-shelf compaction notes from GPT-5.5 and GLM-5.3 are often weak, and RL alone rarely discovers useful note-taking. MEMENTO bootstraps note-taking by SFT on synthetic trajectories with hindsight notes, then RL with answer correctness, note-quality heuristics, and confidence calibration. Trained only to compact into a fresh window, it extends at test time to folding and confidence-based backtracking.

## Key Contributions
1. Trained compaction (hindsight SFT then RL) that keeps a 20K window over books up to 2.5M tokens.

## Empirical Highlights
Qwen3-8B book QA 36.9% to 67.8% with <=20K context; beats GPT-5.5 agent 13.1% / full-book 56.7% at <1/50 the cost; nearly matches a ~100x larger GLM-5.3 agent 69.3% at 1/9 the cost.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.00244`
- Code: none found (`code_status: none`).
