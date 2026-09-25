# ADR 0003: Apache-2.0 code; ship only models trained on permissive, consented data

**Status:** accepted, 2026-09-25

**Decision**
- Code is Apache-2.0, which includes an explicit patent grant.
- A model we distribute may only be trained on data that is both:
  - under a license that allows derived works (for example CC BY 4.0, such as FSboard and PopSign);
  - collected with informed consent.
- Non-commercial datasets (ASL Citizen, WLASL, How2Sign) are for benchmarks only.
- No dataset or weights are committed to git.

**Consequences**
- Released models carry attribution notices for their training data.
- Every dataset is tracked in `dossier/03-datasets.md`.
