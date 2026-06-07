# Dataset — Teman Isyarat

[![Status](https://img.shields.io/badge/status-active-brightgreen)]()

BISINDO (Bahasa Isyarat Indonesia) video dataset for the **Teman Isyarat** project — an AI-powered Indonesian Sign Language recognition system developed by a student team at **Universitas Sebelas Maret (UNS)** in partnership with **GERKATIN Solo**.

> **Note:** The directories `batch-1/` and `batch-2/` currently contain **mock/sample videos** for development and testing. The full production dataset collected with GERKATIN Solo will be added separately.

---

## Dataset Overview

| Attribute | Detail |
|-----------|--------|
| **Language** | BISINDO (Central Java dialect) |
| **Vocabulary** | 20 words |
| **Total Videos** | ~340 |
| **Signers** | 9 unique signers |
| **Batches** | 2 |
| **Format** | MP4 |

---

## Directory Structure

```
dataset/
├── batch-1/               # First recording session
│   ├── farras/            # Signer name (20 words)
│   │   ├── aku/
│   │   │   └── aku.mp4
│   │   ├── apel/
│   │   │   └── apel.mp4
│   │   └── ...            # 18 more words
│   ├── fredi/
│   ├── hani/
│   ├── ian/
│   ├── ivan/
│   ├── mutia/
│   ├── saidah/
│   └── willi/
└── batch-2/               # Second recording session
    ├── farras/
    ├── fredi/
    ├── hany/
    ├── ian/
    ├── ivan/
    ├── kevin/
    ├── mutia/
    ├── saidah/
    └── willi/
```

Each video is organized as `batch-{n}/{signer}/{word}/{word}.mp4`.

---

## Vocabulary (20 words)

| Category | Words |
|----------|-------|
| **Pronouns** | Aku, Kamu, Dia |
| **Greetings & Polite** | Salam, Terima Kasih, Maaf, Nama |
| **Time** | Hari Ini, Besok |
| **Colors** | Merah, Kuning |
| **Family** | Ayah, Ibu |
| **Numbers** | Satu, Dua, Tiga |
| **Social** | Teman |
| **Objects** | Buku |
| **Fruits** | Apel, Pisang |

---

## Signers

| Signer | Batch 1 | Batch 2 |
|--------|:-------:|:-------:|
| Farras | ✓ | ✓ |
| Fredi | ✓ | ✓ |
| Hani / Hany | ✓ | ✓ |
| Ian | ✓ | ✓ |
| Ivan | ✓ | ✓ |
| Kevin | — | ✓ |
| Mutia | ✓ | ✓ |
| Saidah | ✓ | ✓ |
| Willi | ✓ | ✓ |

Each signer contributed **1 video per word** (20 videos per signer per batch).

---

## Data Collection Protocol

- Recorded in a controlled indoor environment with consistent lighting
- Each signer performs the gesture facing the camera from a frontal view
- Videos capture the full upper body including both hands and face
- Recordings were validated by GERKATIN Solo to ensure signing correctness

---

## Usage

### With the Landmark Extraction Pipeline

This dataset is consumed by the [`lm/`](https://github.com/temanisyarat/landmark-extraction) pipeline, which extracts MediaPipe Holistic landmarks (pose + hands) from each MP4 and saves them as `.npz` arrays:

```bash
# From the project root
python lm/process.py --input dataset/mock --output lm/output
```

### With the Training Pipeline

Extracted landmarks are then used by [`model/`](https://github.com/temanisyarat/model-pipeline) for GRU-based training with signer-independent cross-validation.

---

## Future Work

- [ ] Release full production dataset with more signers and repetitions
- [ ] Add per-word repetition samples for increased variability
- [ ] Include challenging conditions (varying backgrounds, lighting)

---

## Acknowledgments

- **GERKATIN Solo** — Dataset validation and field testing with the Deaf community
- **Universitas Sebelas Maret (UNS)** — Hibah Jarprak funding and academic support
