# ai-cyber-lab

Hands-on lab combining machine learning and cybersecurity. Each week has its own notebooks, notes and results.

## Roadmap

| Week | Topic | Status |
|------|-------|--------|
| 1 | Setup + first image classifier (fast.ai Lesson 1) + TryHackMe Pre-Security | In progress |

## Week 1

- [x] Repo + Colab environment
- [x] Run fast.ai Lesson 1 notebook as is
- [x] Train my own classifier (custom classes)
- [ ] TryHackMe: first 3 Pre-Security rooms

### Results

| Experiment | Classes | Images (train / valid) | Model | Accuracy |
|-----------|---------|------------------------|-------|----------|
| Lesson 1 baseline (bird vs forest) | 2 | 103 / 25 | resnet18 | 0.92 (23/25 on validation) |
| Custom classifier (phishing login vs real login) | 2 | 105 / 26 | resnet18 | 1.00 (26/26 on validation) |

> Note: the validation sets are small (25 and 26 images), so each wrong prediction costs about 4% accuracy. Treat the numbers as approximate; they can shift a few points between runs. A 100% score on 26 images does not mean the model is perfect.

### Data collection notes

- **Baseline:** images of `bird` and `forest` downloaded with a web image search (`ddgs`), 128 images in total after removing broken downloads.
- **Split:** 80% train / 20% validation, random split with a fixed seed (42).
- **Training:** `resnet18`, pretrained, `fine_tune(3)` on a Colab T4 GPU.
- **Custom classifier:** `phishing_login` vs `real_login`, 131 images in total (105 train / 26 validation), collected with the same web image search (one query per class: "phishing login page screenshot" and "bank login page screenshot"). Same model and training setup as the baseline.
- **Caveats:** search results are noisy (some images may not be real login pages) and may contain duplicates or near-duplicates, which can leak between train and validation and inflate accuracy. Labels were not manually verified, so the 100% result should be read as "works on this small, noisy set", not as a reliable phishing detector.

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
