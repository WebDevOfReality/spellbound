# 04: Prior art

## Fingerspelling.xyz (Hello Monday / DEPT × American Society for Deaf Children, 2021)

The closest prior art to our first slice.
- **What it is:** a free browser app. The webcam plus **MediaPipe Hands** track the learner's hand
  while they form ASL alphabet letters, and it gives instant feedback on accuracy. It shows a 3-D hand
  model to copy.
- **Who it's for:** it explicitly targets **parents of deaf children**.
- **Traction:** 150k correct signs in its first 10 days, and more than 5.5M after 10 months.
- **What we take from it:**
  - The approach works in a browser on ordinary hardware.
  - The family audience is real.
  - Gamified levels help.
- **What's different for us:**
  - It's open source, and the model and data pipeline are ours to improve.
  - We iterate beyond fingerspelling.
  - Deaf advisors are in the loop.
  - It's tunable for school devices.
- Sources:
  - [ASDC announcement](https://deafchildren.org/2021/05/asdc-fingerspelling-app/)
  - [fingerspelling.xyz](https://fingerspelling.xyz/)
  - [DEPT case study](https://www.deptagency.com/case/a-pioneering-approach-to-teaching-the-sign-language-alphabet/)
  - [Dezeen](https://www.dezeen.com/2021/08/27/fingerspelling-xyz-app-learn-sign-language-alphabet-design/)

## PopSign (Georgia Tech + Google)

- **What it is:** a smartphone bubble-shooter game that helps **hearing parents of deaf infants**
  practice signs. It uses in-game sign recognition.
- **Its dataset:** it produced the PopSign ASL v1.0 dataset (see [03](03-datasets.md)).
- **Lesson:** games keep parents practicing, and one-handed phone signing is a realistic input.
- Source: [NeurIPS 2023](https://proceedings.neurips.cc/paper_files/paper/2023/hash/00dada608b8db212ea7d9d92b24c68de-Abstract-Datasets_and_Benchmarks.html)

## Kaggle competitions (Google, 2023)

- **Two competitions:** Isolated Sign Recognition (GISLR, 250 signs) and Fingerspelling Recognition.
- **The top solutions** are small transformer and conv models over **MediaPipe landmarks**, sized to
  run on phones.
- **Lesson:** landmark-based models are the proven efficient path. The winning write-ups are a free
  architecture reference.
- Sources:
  - [1st place fingerspelling](https://github.com/ChristofHenkel/kaggle-asl-fingerspelling-1st-place-solution)
  - [TF blog](https://blog.tensorflow.org/2023/05/american-sign-language-fingerspelling-recognition.html)

## Open-source fingerspelling interface (2024)

- An academic open-source ASL fingerspelling recognizer with semantic pose retrieval.
- It's worth reading for architecture and for its UI choices.
- Source: [arXiv 2408.09311](https://arxiv.org/pdf/2408.09311)

## What failed: sign-language gloves

See [01](01-deaf-community-and-ethics.md). The lesson: when hearing developers set the scope without
Deaf involvement, the product gets rejected.
