# ADR 0002: Classify hand landmarks, not raw pixels

**Status:** accepted, 2026-09-25

**Context**
- The open ASL datasets (FSboard, the Kaggle sets) are distributed as MediaPipe landmarks.
- The winning Kaggle solutions are small landmark models.
- Pixel models are larger, and they risk learning skin tone, lighting and background.

**Decision**
- Classifiers take normalized MediaPipe hand landmarks as input. Later they also take face and pose
  landmarks.

**Consequences**
- Models are tiny and fast.
- We depend on MediaPipe's tracking quality: thumb occlusion hurts A/S/T/M/N.
- Landmarks from different MediaPipe versions may differ. Check before mixing data.
- Pixel-level feedback (such as "your thumb is hidden") has to be inferred from landmarks.
