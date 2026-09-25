# Dossier: discovery for Spellbound

This is the collected findings from planning and discovery: one topic per file, with sources cited.
It's a living record, so update it when we learn something, and mark anything unverified as
**(unverified)**.

| # | File | Question it answers |
|---|---|---|
| 01 | [Deaf community & ethics](01-deaf-community-and-ethics.md) | Who is this for, and how do we avoid building a "sign glove"? |
| 02 | [ASL linguistics primer](02-asl-linguistics-primer.md) | What is fingerspelling, and what makes it hard to recognize? |
| 03 | [Datasets](03-datasets.md) | What data exists, under what license, and collected with what consent? |
| 04 | [Prior art](04-prior-art.md) | What has been built already, and what can we learn from it? |
| 05 | [Models & runtimes](05-models-and-runtimes.md) | How do we recognize hands cheaply, and where does Opus 5.5 fit? |
| 06 | [Hardware targets](06-hardware-targets.md) | What must it run on? |
| 07 | [Questions for our interpreter advisor](07-questions-for-advisor.md) | What we need to learn from people in the field |

## Summary: what discovery told us (2026-09-25)

1. **The need is real and specific.** About 95% of deaf children have hearing parents. Early language
   access matters enormously, and families often learn ASL late. A good practice tool for *families*
   is a well-grounded first target.
2. **Fingerspelling practice with a webcam is proven feasible.** Fingerspelling.xyz (with the
   American Society for Deaf Children, 2021) did exactly this in a browser with MediaPipe Hands, and
   logged millions of correct signs. We're not inventing the approach. Our contribution is
   **open source, on-device, iterative and community-guided**, with a path beyond fingerspelling.
3. **Good open data exists.** FSboard (Google + DPAN, 147 Deaf signers, CC BY 4.0) and PopSign
   (CC BY 4.0) were collected with consent. Several popular datasets (WLASL, How2Sign, ASL Citizen)
   are **non-commercial only**, so we'll keep them out of anything we ship.
4. **The Deaf community has seen many hearing-led "translators" fail.** Co-design and honest scope
   are requirements, not nice-to-haves.
