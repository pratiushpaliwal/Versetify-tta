# Citations

At least three recent (2022–2026) primary papers that use, extend, test, or rely on the selected concept (Test-Time Adaptation), as required. Six are listed; each entry states exactly which claim in the artifact it supports.

1. **A. Kosowski, P. Uznański, J. Chorowski, Z. Stamirowska, M. Bartoszkiewicz.** *The Dragon Hatchling: The Missing Link between the Transformer and Models of the Brain.* arXiv:2509.26507, 2025.
   Used for: BDH's architecture, its Hebbian/synaptic reformulation of attention, sparse-activation and scale-free-connectivity claims, and its GPT-2-matched scaling behavior (Tab 4).

2. **Pathway Research.** *BDH-CQ: In-Context Learning with Recurrent Latent Reasoning.* arXiv:2608.09888, 2026.
   Used for: the core claim of this artifact — BDH-CQ's recurrent-state, no-parameter-update adaptation mechanism; the 150M-parameter, 29.5% pass@2 ARC-AGI-1 result at $0.0007/task (Tab 4, one-page summary).

3. **Pathway.** *Pathway's 150M-Parameter Model Breaks the ARC-AGI-1 Cost-Efficiency Frontier* (company research announcement accompanying source 2), 2026.
   Used for: framing the BDH-CQ result as a cost-efficiency frontier point rather than an accuracy record, and the comparison to GPT-5.6-class systems (Tab 4, evidence-discipline table).

4. **G. Wang, J. Li, Y. Sun, X. Chen, C. Liu, Y. Wu, M. Lu, S. Song, Y. Abbasi-Yadkori.** *Hierarchical Reasoning Model.* arXiv:2506.21734, 2025.
   Used for: the "optimization route" baseline — HRM's two-timescale recurrent architecture, ~27M parameters, ~1,000 examples per task, and its reported ARC-AGI performance (Tab 4, Tab 3 contrast framing).

5. **A. Jolicoeur-Martineau.** *Less is More: Recursive Reasoning with Tiny Networks.* arXiv:2510.04871, 2025. (ARC Prize 2025 Paper Award, 1st place.)
   Used for: TRM's simplified recursive-refinement architecture and its reported 45% (ARC-AGI-1) / 8% (ARC-AGI-2) accuracy at ~7M parameters (Tab 4).

6. *Test-Time Adaptation of Tiny Recursive Models.* arXiv:2511.02886, 2025.
   Used for: a direct, named example of the optimization route to test-time adaptation — full fine-tuning, embeddings-only tuning, and LoRA-style adaptation of a TRM checkpoint, all requiring a gradient computed against the specific evaluation task (Tab 4, Tab 3 contrast table).

## Background / secondary consultation (not load-bearing for any specific number)

- ARC Prize 2024 Technical Report, arXiv:2412.04604 — used only to confirm that test-time training is described as the dominant paradigm for LLM-based ARC-AGI solutions as of that report, motivating why the artifact contrasts an optimization route against a state-accumulation route.
- Zirui Ren, Ziming Liu, *Are Your Reasoning Models Reasoning or Guessing? A Mechanistic Analysis of Hierarchical Reasoning Models* — used to source the "documented failure modes on trivially simple puzzles" limitation attributed to HRM in Tab 4 and Tab 6, so that HRM's strengths are not presented without a known counterpoint.

## Note on evidence level

Per the track's accuracy requirement: all benchmark numbers above are **developer-reported** results from the cited primary sources. Where a third-party reproduction or audit is mentioned (the reported black-box audit of BDH-CQ's ARC-AGI-1 score), this is stated explicitly as a partial independent check, not a full independent replication of methodology, and is distinguished from a benchmark, a deployment, and a commercial partnership per the track's evidence-labeling guidance.
