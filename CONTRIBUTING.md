# Contributing to Spellbound

Thanks for being here. Spellbound is early (iteration 0) and moves in small iterations.

## Who we most want to hear from

- **Deaf signers, ASL teachers and interpreters.** Your judgment decides what "correct" means.
  Open an issue, even just to say something feels wrong.
- **Families learning ASL.** Tell us what you actually struggle with.
- **Developers and ML folks.** Pick an issue labeled `good first issue` or `help wanted`.

## Ground rules

- **Never add personal signing video or landmarks of real people** to this repo unless they have
  given informed consent under a license that allows it. Never add data of minors.
- **Record where data comes from.** Any dataset or model we use gets an entry in
  [dossier/03-datasets.md](dossier/03-datasets.md) with its license and consent model.
- **Keep it on-device.** Features must not upload camera video. Anything that sends data
  anywhere must be opt-in and documented.
- **Small PRs, one idea each.** Big direction changes start as a short ADR in `docs/decisions/`.

## Development

Setup instructions will land with iteration 1. Planned tooling: Node LTS for the web app, and
[uv](https://docs.astral.sh/uv/) + Python for training.

## Commit style

Use short imperative subjects, for example `dossier: add PopSign license notes`. Use prefixes such as
`dossier:`, `docs:`, `spike:`, `web:` or `train:` where they help.
