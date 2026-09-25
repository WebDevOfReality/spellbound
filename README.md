# Spellbound

**An open-source ASL fingerspelling trainer: on-device, free, and built with Deaf educators and families.**

About 95% of deaf and hard-of-hearing children are born to hearing parents
([Mitchell & Karchmer, 2004](https://eric.ed.gov/?id=EJ747626)). Many of those families are learning
ASL at the same time as their kids. Spellbound starts small: a learner fingerspells to a webcam and
gets instant, friendly feedback. It runs in the browser on ordinary school and home devices, and
**video never leaves the device**.

> **Status:** iteration 0 (discovery). There's nothing to install yet. See the [roadmap](docs/roadmap.md).

## What this is, and what it is not

- **It is** a practice tool for learners, especially hearing family members of Deaf kids, and a place
  to grow toward vocabulary practice and, much later, translation research.
- **It is not** an interpreter and not a replacement for qualified human interpreters, Deaf teachers,
  or ASL classes. ASL is a full language with its own grammar, facial grammar, and use of space.
  Fingerspelling is a small part of it.
- **It is built with** the Deaf community, not just for them. See
  [dossier/01-deaf-community-and-ethics.md](dossier/01-deaf-community-and-ethics.md).

## Guiding constraints

1. **Open source.** Code is Apache-2.0. Datasets keep their own licenses; see
   [dossier/03-datasets.md](dossier/03-datasets.md).
2. **Runs on modest hardware.** It's browser-first and targets Chromebook-class machines and phones.
3. **Iterate in small steps.** We prove each idea with a big model or a simple baseline first, then
   make it small and efficient.

## Repo map

| Path | What's there |
|---|---|
| [dossier/](dossier/00-index.md) | Discovery research: community and ethics, ASL primer, datasets, prior art, models, hardware |
| [docs/roadmap.md](docs/roadmap.md) | Iterations and what "done" means for each |
| [docs/technical-direction.md](docs/technical-direction.md) | Rough architecture, v0 |
| [docs/decisions/](docs/decisions/) | Short architecture decision records (ADRs) |
| [spikes/](spikes/) | Throwaway experiments. Each one has a README saying what it showed. |

## Contributing

We especially welcome Deaf signers, ASL teachers, interpreters and families. See
[CONTRIBUTING.md](CONTRIBUTING.md) and our [Code of Conduct](CODE_OF_CONDUCT.md).

## License

Code: [Apache-2.0](LICENSE). Third-party datasets and models keep their own licenses.
