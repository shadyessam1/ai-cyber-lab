# ai-cyber-lab

Hands-on lab combining machine learning and cybersecurity. Each week has its own notebooks, notes and results.

## Roadmap

| Week | Topic | Status |
|------|-------|--------|
| 1 | Setup + first image classifier (fast.ai Lesson 1) + TryHackMe Pre-Security | In progress |

## Week 1

- [x] Repo + Colab environment
- [x] Run fast.ai Lesson 1 notebook as is
- [ ] Train my own classifier (custom classes)
- [ ] TryHackMe: first 3 Pre-Security rooms

### Results

| Experiment | Classes | Images (train / valid) | Model | Accuracy |
|-----------|---------|------------------------|-------|----------|
| Lesson 1 baseline (bird vs forest) | 2 | 103 / 25 | resnet18 | 0.92 (23/25 on validation) |
| Custom classifier | _TBD_ | _TBD_ | resnet18 | _TBD_ |

> Note: the validation set is small (25 images), so each wrong prediction costs 4% accuracy. Treat the number as approximate; it can shift a few points between runs.

### Data collection notes

- **Baseline:** images of `bird` and `forest` downloaded with a web image search (`ddgs`), 128 images in total after removing broken downloads.
- **Split:** 80% train / 20% validation, random split with a fixed seed (42).
- **Training:** `resnet18`, pretrained, `fine_tune(3)` on a Colab T4 GPU.
- **Custom classifier:** _TBD. Write here where the images came from, how many per class, and any cleaning done._

## Structure

```
ai-cyber-lab/
├── notebooks/
│   └── 01_fastai_lesson1.ipynb
├── week1/
│   └── notes.md
├── requirements.txt
└── README.md
```

## Running on Colab

Open the notebook from GitHub in Colab (Runtime -> Change runtime type -> T4 GPU), then Run all.
