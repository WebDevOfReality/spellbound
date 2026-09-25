# 05: Models & runtimes

## Perception: MediaPipe HandLandmarker (Tasks API)

- **What it gives us:** 21 hand landmarks per hand, in normalized image coordinates plus "world"
  3-D coordinates, from images or live video. It runs in the browser via the
  `@mediapipe/tasks-vision` npm package, on WASM with an optional GPU delegate.
- **License:** Apache-2.0.
- **What it's used for:** Fingerspelling.xyz, the Kaggle datasets (the 0.9 legacy version) and FSboard
  all build on MediaPipe landmarks. So our training data and our runtime share a representation.
- **Later:** the face and pose landmarkers (Holistic) add non-manual markers for sign vocabulary.
- Sources:
  - [Web guide](https://ai.google.dev/edge/mediapipe/solutions/vision/hand_landmarker/web_js)
  - [npm](https://www.npmjs.com/package/@mediapipe/tasks-vision)

## Recognition: a ladder of models (small first)

| Rung | Model | Input | Good for |
|---|---|---|---|
| 0 | Nearest-neighbor / rules on normalized landmarks | one frame | Proving the pipeline, and instant "record your own examples" |
| 1 | Small MLP (~10–50k params) | one frame, normalized + mirrored | Static letters (24) |
| 2 | Tiny temporal model (1-D conv / GRU / small transformer) | ~1 s landmark window | J, Z, and word spelling |
| 3 | Kaggle-winner-style conformer over landmark sequences | sequences | Continuous fingerspelling (FSboard) |

**Normalization (a key design choice).** Steps:
1. Translate to the wrist.
2. Scale by palm size.
3. Mirror left hands to right.
4. **Keep rotation information**, because orientation distinguishes G/H/P/Q (see
   [02](02-asl-linguistics-primer.md)).

## Where Opus 5.5 fits

1. **Build partner.** It writes the code, dossier and experiments.
2. **Ceiling baseline.** Send held-out letter frames to Opus 5.5 vision and ask what letter each is.
   That tells us how good a frontier general model is *without* training. If our tiny model beats
   it, that's a strong signal. If Opus is poor at this, that's a finding too: generic vision models
   don't know fingerspelling.
3. **Coach.** It turns structured classifier output (for example: target N, predicted M, thumb
   between the wrong fingers) into warm, age-appropriate feedback text. It's optional, and it moves to
   a local LLM on the MSI laptop (`qwen3:8b` via Ollama) as the "efficiency" step. **Only structured
   results are sent to it, never images of kids.**

## Export & runtime

- Train in **PyTorch** (uv-managed Python) on the RTX 4070 laptop.
- Export to **ONNX** and run with `onnxruntime-web` (WASM/WebGPU). Alternatively use TF.js.
- Quantize to int8 in iteration 4. Target a model under 1 MB for static letters.

## Fairness

Sign-recognition models show biases across signer demographics
([Studying and Mitigating Biases in Sign Language Understanding Models, 2024](https://arxiv.org/pdf/2410.05206)).
We'll report accuracy per group where the data allows, and test with different skin tones and
lighting, including webcam-quality video.
