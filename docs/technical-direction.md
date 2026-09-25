# Technical direction (v0, rough)

```
 ┌──────────────── browser (all camera processing stays here) ────────────────┐
 │ webcam ─► MediaPipe HandLandmarker ─► normalize ─► letter model (ONNX) ─► UI  │
 │              (21 pts/frame)          (wrist-origin,   (MLP → temporal)   │     │
 │                                       mirror, scale)                   feedback
 └──────────────────────────────────────────────────────────────────────┼──────┘
                                        structured result only (opt.)   ▼
                                                        coach LLM: Opus 5.5 → local qwen3:8b
```

## Principles

1. **Browser-first, on-device** ([ADR 0001](decisions/0001-browser-first.md)).
2. **Landmarks, not pixels** ([ADR 0002](decisions/0002-landmarks-not-pixels.md)). This makes the
   models tiny and invariant to skin tone and background, and it matches the open datasets.
3. **Prove big, then shrink.** The first prototype of any capability may use Opus 5.5. Each capability
   then gets a small-model rung, measured against that ceiling.
4. **Data licenses are separate from code** ([ADR 0003](decisions/0003-licenses.md)).

## Planned layout

```
web/     Vite + TypeScript static app, @mediapipe/tasks-vision, onnxruntime-web
train/   uv + PyTorch: loaders (FSboard), normalization, models, eval, ONNX export
shared/  normalization spec + test vectors, so Python and TS normalize identically
spikes/  throwaway experiments
```

**Risk: Python and TS normalization drift.** `shared/` holds golden input/output landmark files, and
both sides test against them.

## Stack choices (defaults; can change via ADR)

| Concern | Choice | Why |
|---|---|---|
| Hand tracking | MediaPipe Tasks (web) | Apache-2.0, fast on CPU, and the same representation as our data |
| Web app | Vite + TypeScript, no framework at first | A small, static page with no framework to learn |
| Training | Python 3.12 via uv, PyTorch (CUDA) | Standard tooling, and the laptop GPU is enough |
| Browser inference | onnxruntime-web | Takes models from any framework, and supports WASM and WebGPU |
| Hosting | GitHub Pages | Free and static. HTTPS is required for camera access. |
| Coach LLM | Opus 5.5 → Ollama `qwen3:8b` on w3b-weavr | Prove big, then go local |
