# Test-Time Adaptation, Live: State vs. Weights
**DataForge 2026 × Pathway Track — Team Versetify**

Live artifact: `index.html` (open directly in any browser, no build step, no sign-in, no network calls).

- **Public artifact URL:** [https://pratiushpaliwal.github.io/Versetify-tta/](https://versetify.vercel.app/)
- **Public source code repository:** https://github.com/pratiushpaliwal/Versetify-tta

## Deployment

1. **Repo:** create a new public GitHub repository, upload every file in this folder (drag-and-drop works on github.com — no git command line needed). Copy the repo's URL.
2. **Live URL:** in that repo, go to **Settings → Pages**, under "Build and deployment" set **Source: Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**. GitHub gives you a URL like `https://<username>.github.io/<repo-name>/` within a minute or two — that opens `index.html` automatically without sign-in.
3. Come back to this README and replace the two placeholder lines above with the real links.

## The one-sentence claim

> A system can acquire a new input→output rule from a handful of demonstrations by **additively accumulating a bounded matrix of state** at inference time — zero gradient steps, zero backward passes — and this works well until the number of distinct patterns it must hold exceeds the dimensionality of that state, at which point recall degrades through cross-talk, not through "running out of layers."

This is the Test-Time Adaptation topic from the approved list, and it is chosen specifically because the track brief's own framing of the topic — "BDH-CQ is the counterexample: no evaluation-task demonstrations in training and no parameter updates at inference, with adaptation happening in recurrent state rather than in weights" — is a claim a learner can watch happen, cell by cell, rather than just read about.

## Intended learner and prerequisites

- **Audience:** undergraduate ML students, hackathon judges, or engineers who know what a matrix multiply and a single gradient-descent step are, but have not necessarily seen fast-weight / Hebbian associative memory before.
- **Prerequisites:** vectors and dot products; the idea of a loss function; no prior knowledge of BDH, ARC-AGI, or recurrent state required — these are introduced inline.

## Learning objectives

By the end, a learner should be able to:
1. State the difference between "state that accumulates additively per demonstration" and "weights updated by gradient descent," in their own words.
2. Predict, before running it, whether a given (K colors, D dimensions) setting will recall correctly or suffer cross-talk.
3. Name the specific role BDH-CQ's recurrent memory and BDH's Hebbian attention play relative to HRM/TRM's gradient-based test-time adaptation, and cite the primary source for each claim.
4. Recognize at least one limitation of the fast-weight mechanism (capacity bound by dimension) and one open limitation of the real systems (BDH-CQ's frontier point is a cost-efficiency result, not an accuracy record; HRM has documented failure modes on trivial cases).

## Architecture of the artifact

Single static HTML file, six tabs, no external dependencies, no server:

| Tab | What it is | Live / Reported / Illustration |
|---|---|---|
| 1. Live fast-weight memory | A toy linear associative (Hebbian) memory: `W += v·kᵀ` per demonstration, retrieval by nearest stored key. Real vector math executed in the browser on every click. | **Live** |
| 2. Capacity limit | A sweep over K (number of colors) at fixed D (vector dimension), averaging accuracy over 30 random trials per K value, rendered as an inline SVG bar chart computed on the fly. | **Live** |
| 3. Optimization contrast | A tiny softmax classifier trained by real, hand-written batch gradient descent (manual cross-entropy gradient, no library) on the same demonstration pairs, for a learner-chosen number of steps. | **Live** (explicitly labeled as a pedagogical toy, not a reproduction of HRM/TRM) |
| 4. BDH / BDH-CQ module | Prose explanation of BDH's Hebbian/synaptic attention and BDH-CQ's recurrent-latent-reasoning result on ARC-AGI-1, with every number attributed to a cited primary source. | **Reported**, sourced, no live computation |
| 5. Explain it back | Free-text reflection box (local only, nothing submitted anywhere) plus a self-test with a revealable model answer. | N/A |
| 6. Limitations & sources | Explicit scope statement plus the full reference list. | N/A |

**Nothing is animated for effect.** The matrix heatmap in Tab 1, the bar chart in Tab 2, and the loss curve in Tab 3 are all direct renders of numbers computed in that page load, in your browser, from the sliders you set.

### Role of every major component (for judges' live-defense questions)

- `mulberry32` — a small seeded PRNG so keys are reproducible for a given seed and regenerated on "Reshuffle keys."
- `state.keys` — K unit vectors in R^D, standing in for "colors." These are the only stochastic input; everything downstream is deterministic linear algebra.
- `state.perm` — the hidden rule π being taught, chosen by the rule dropdown.
- `state.W` — the accumulated D×D fast-weight matrix; this **is** the "recurrent state" the whole artifact is about.
- `learnStep()` — adds one outer product per demonstration; this is the entire "training" procedure for Tabs 1–2.
- Tab 3's `Wc` (K×D) — a genuinely separate, randomly-initialized weight matrix trained by explicit gradient descent; used only to make the mechanism contrast concrete.

## How to reproduce the numbers in Tab 4

Every figure in Tab 4 (BDH parameter-matching to GPT-2, BDH-CQ's 29.5% pass@2 at $0.0007/task, HRM's ~27M-parameter result, TRM's 45%/8% ARC-AGI-1/2 result, the TRM test-time-adaptation strategies) is taken directly from the primary papers listed below and in `CITATIONS.md`, and is not independently re-run by this team — the track brief explicitly does not expect teams to reproduce unpublished or unavailable BDH/BDH-CQ checkpoints. No number in Tab 4 is presented as this team's own result.

## What is NOT claimed

- This artifact does not run, fine-tune, or reproduce BDH, BDH-CQ, HRM, or TRM.
- The Tab 1–3 toy systems are built from scratch for this submission; they illustrate a mechanism, not a benchmark result.
- BDH-CQ's ARC-AGI-1 number is a cost-efficiency frontier point, not the highest published accuracy on that benchmark — this is stated explicitly in Tab 4 and in the one-page summary.

## Files in this package

```
index.html                      the interactive artifact (open this)
README.md                       this file
one-page-concept-summary.pdf    the required 1-page concept summary
CITATIONS.md                    full reference list with roles
AI_DISCLOSURE.md                AI-assistance, code, and asset disclosure
SOURCES_AND_LICENSES.md         source/license record for every reused component
```

## Credits and licenses

- All code in `index.html` is original, written for this submission, and is released under the MIT License (see `SOURCES_AND_LICENSES.md`).
- No third-party code, fonts, images, or datasets are embedded. The page uses only system fonts and inline SVG generated by its own script.
- Figures and claims about BDH, BDH-CQ, HRM, and TRM are paraphrased from the cited primary sources; no text is reproduced verbatim beyond short attributed technical terms.
