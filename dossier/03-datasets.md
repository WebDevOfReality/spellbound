# 03: Datasets

**Rule:** a dataset can be used for *shipped* models only if its license allows redistribution and
derived models, and it was collected with informed consent. **Non-commercial (NC)** datasets can be
used for research benchmarks, but not to train anything we ship, because a released model's
downstream use is out of our control.

| Dataset | What | Scale | License | Consent | Use in Spellbound |
|---|---|---|---|---|---|
| **FSboard** (Google + DPAN) | Continuous fingerspelling, phone selfie cameras | 147 Deaf signers, >3M characters, >250 h | **CC BY 4.0** | Paid, consenting Deaf signers | ✅ **Primary** candidate for fingerspelling |
| **Kaggle ASL Fingerspelling** comp. (2023) | MediaPipe 0.9 hand+face+pose landmarks of fingerspelled phrases | 100+ Deaf signers | Competition data rules **(unverified)**; FSboard appears to be the public release of this data | Recruited Deaf signers, de-identified landmarks | Prefer FSboard; confirm the license on the Kaggle page |
| **PopSign ASL v1.0** (Georgia Tech + Google) | 250 isolated signs, one-handed smartphone video | 47 Deaf signers, >210k examples | **CC BY 4.0** (per paper) | Consenting Deaf adults | ✅ Candidate for isolated signs (iteration 5+) |
| **GISLR** (Kaggle "asl-signs", 2023) | 250 isolated signs, 543 MediaPipe landmarks per frame | 21 participants | **(unverified)**, competition rules | (unverified) | Check before use |
| **ASL Citizen** (Microsoft) | Isolated signs for dictionary lookup | 52 signers, 83k videos, 2,731 signs | Microsoft Research license, **non-commercial** | Exemplary: Deaf-led, ASL-first consent | 🔬 Benchmark only |
| **WLASL** | Word-level signs scraped from the web | ~2,000 glosses | **C-UDA**, academic, **non-commercial** | Scraped (no participant consent) | 🔬 Benchmark only, or skip |
| **How2Sign** | Continuous ASL, multi-view, with English | ~80 h | **CC BY-NC 4.0** | Recruited signers | 🔬 Translation research only |

## Our own data (later)

- We start with **zero self-collected data**. The first training uses FSboard.
- If we collect data later (for example, "donate your signing" from adult volunteers), it'll be:
  - landmarks only (no video)
  - opt-in
  - adults only
  - with an ASL-first consent flow modeled on ASL Citizen
  - under a clear license

## Sources

- FSboard: [arXiv 2407.15806](https://arxiv.org/abs/2407.15806), [Kaggle](https://www.kaggle.com/datasets/googleai/fsboard)
- Kaggle fingerspelling competition: [kaggle.com/competitions/asl-fingerspelling](https://www.kaggle.com/competitions/asl-fingerspelling), [TensorFlow blog](https://blog.tensorflow.org/2023/05/american-sign-language-fingerspelling-recognition.html), [1st-place solution](https://github.com/ChristofHenkel/kaggle-asl-fingerspelling-1st-place-solution)
- PopSign: [NeurIPS 2023 D&B](https://proceedings.neurips.cc/paper_files/paper/2023/hash/00dada608b8db212ea7d9d92b24c68de-Abstract-Datasets_and_Benchmarks.html)
- GISLR: [kaggle.com/competitions/asl-signs](https://www.kaggle.com/competitions/asl-signs)
- ASL Citizen: [Microsoft Research](https://www.microsoft.com/en-us/research/publication/asl-citizen-a-community-sourced-dataset-for-advancing-isolated-sign-language-recognition/), [arXiv 2304.05934](https://arxiv.org/abs/2304.05934)
- WLASL: [GitHub](https://github.com/dxli94/WLASL)
- How2Sign: [how2sign.github.io](https://how2sign.github.io/)

## TODO

- [ ] Verify the Kaggle competition and GISLR licenses directly on Kaggle. The web fetch was blocked
      during discovery, so this needs a Kaggle login.
- [ ] Download the FSboard sample and document its landmark format. Is it the same as MediaPipe
      Tasks' HandLandmarker? The version difference 0.9 → current may shift coordinates.
