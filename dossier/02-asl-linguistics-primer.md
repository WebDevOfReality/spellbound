# 02: ASL linguistics primer (for builders)

This is a working primer for the engineering side. Our advisor corrects it, not the other way round.

## Fingerspelling in context

- ASL is a complete natural language, not signed English. Fingerspelling spells English words
  letter by letter using the **manual alphabet**. It's used for names, places, brand names, English
  terms without an established sign, and some borrowed forms.
- Fluent fingerspelling is **fast and co-articulated**: letters blend into word shapes rather than
  being held one by one. Real-world fingerspelling recognition is therefore a *sequence* problem.
  FSboard and the Kaggle competition target continuous phrases for this reason
  ([FSboard paper](https://arxiv.org/abs/2407.15806)).
- **Learners** start with individual, held letters. That's where Spellbound starts too, and it's
  why iteration 1 is static letters.

## The 26 letters, as a recognition problem

- **24 static handshapes** and **2 with motion**: **J** traces a J with the pinky, and **Z** traces
  a Z with the index finger. J and Z need a temporal model, which is iteration 3.
- **Orientation matters, not just shape.** Examples (to verify with our advisor):
  - **G/H** are sideways.
  - **P** is K pointed down.
  - **Q** is G pointed down.
  - So features must keep palm orientation and not normalize it away.
- **Known look-alike groups** (to verify with our advisor): **A/S/T/M/N/E** (closed fists that differ
  in thumb placement), **U/V/R/K**, **D/F**, **I/Y**, **C/O**. Thumb occlusion makes the first group
  hard for 2-D cameras.
- **Handedness.** Signers use their dominant hand, and left-handed signing mirrors. The model should
  mirror-normalize, and the UI should let the learner pick a hand.

## Beyond fingerspelling (later iterations)

- **Isolated signs** combine handshape, location, movement, palm orientation, and **non-manual
  markers** (face, mouth, eyebrows, head). That's why later iterations need the face and pose too.
- **Continuous signing and translation** uses space, classifiers, role shift and facial grammar. This
  is open research, so it's a long-range goal rather than a roadmap promise.

## To confirm with our advisor

- Which letters do beginners confuse most in practice?
- How strict should feedback be? Is "close enough" encouraging, or does it build bad habits?
- Regional or school-specific conventions we should know about.
