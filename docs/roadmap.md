# Roadmap

**The target is all of ASL.** Fingerspelling (iterations 1–4) is the proof of concept. It builds and
proves the camera → landmarks → small model → feedback pipeline. Later iterations extend that
pipeline to signs, movement, facial grammar and sentences.

Small iterations. Each one has a single goal and a concrete "done when". We don't start the next
iteration until the current one's done-when is true, or until we've written down why we're changing
course (as an ADR in `decisions/`).

| Iter | Goal | Done when | Status |
|---|---|---|---|
| **0** | Discovery: dossier, roadmap, technical direction, dev env, repo | Repo public ✅, dossier filled ✅, questions sent to our advisor, landmark spike runs | **in progress** |
| **1** | **Static letters.** Recognize the 24 static letters live from a webcam | The browser page shows a live letter guess, and accuracy is measured on held-out FSboard signers. Opus 5.5 vision is measured on the same set as a ceiling. | next |
| **2** | **Trainer loop.** Prompt a letter → learner signs → check → feedback | Our advisor and at least one family learner have tried it, and their feedback is recorded in the dossier | |
| **3** | **Motion + words.** J/Z and spelling short words (temporal model) | Spells 3–5-letter words end-to-end at learner speed | |
| **4** | **Efficiency pass.** Quantize, measure, and optimize on low-end devices | Smooth (≥15 fps) on a Chromebook-class device. The coach runs on a local LLM. | |
| **5** | **Receptive practice.** Read fingerspelled words (shown via video or an avatar) | Depends on our advisor's answer to question 8 | |
| **6+** | **Vocabulary.** Isolated signs (PopSign-style), with face and pose | Driven by feedback | |
| ∞ | Continuous sign ↔ English translation | Research track, not a promise | |

## Iteration 1 — broken down

1. Download the FSboard sample. Document its landmark format in `dossier/03`.
2. `train/`: uv project. Dataset loader, then extract single-letter frames (the hard part:
   continuous data needs letter alignment, so start from slow, clearly segmented spellings), then
   normalize, then run the MLP baseline.
3. Evaluate on **held-out signers**, not held-out frames, so the model isn't just memorizing people.
4. Measure Opus 5.5 on the same frames (the ceiling baseline).
5. Export to ONNX, then build `web/`: a live letter guess on top of spike 00.
