# ai-cyber-lab

Hands-on lab combining machine learning and cybersecurity. Each week has its own notebooks, notes and results.

## Roadmap

| Week | Topic | Status |
|------|-------|--------|
| 1 | Setup + first image classifier (fast.ai Lesson 1) + TryHackMe Pre-Security | Done |
| 2 | Deploy the model as a demo (fast.ai Lesson 2) + Professor Messer threats + 2 more THM rooms | Done |

## Week 1

- [x] Repo + Colab environment
- [x] Run fast.ai Lesson 1 notebook as is
- [x] Train my own classifier (custom classes)
- [x] TryHackMe: first 3 Pre-Security rooms

### Results

| Experiment | Classes | Images (train / valid) | Model | Accuracy |
|-----------|---------|------------------------|-------|----------|
| Lesson 1 baseline (bird vs forest) | 2 | 103 / 25 | resnet18 | 0.92 (23/25 on validation) |
| Custom classifier (phishing login vs real login) | 2 | 105 / 26 | resnet18 | 1.00 (26/26 on validation) |
| Bird vs forest v2 (more varied search queries, deployed as demo) | 2 | 187 / 46 | resnet18 | 0.98 (45/46 on validation) |

> Note: the validation sets are small (25 and 26 images), so each wrong prediction costs about 4% accuracy. Treat the numbers as approximate; they can shift a few points between runs. A 100% score on 26 images does not mean the model is perfect.

### Data collection notes

- **Baseline:** images of `bird` and `forest` downloaded with a web image search (`ddgs`), 128 images in total after removing broken downloads.
- **Split:** 80% train / 20% validation, random split with a fixed seed (42).
- **Training:** `resnet18`, pretrained, `fine_tune(3)` on a Colab T4 GPU.
- **Custom classifier:** `phishing_login` vs `real_login`, 131 images in total (105 train / 26 validation), collected with the same web image search (one query per class: "phishing login page screenshot" and "bank login page screenshot"). Same model and training setup as the baseline.
- **Bird vs forest v2 (Week 2):** the first demo model said "bird" for every forest photo I tried, even though validation accuracy was 92%. The validation score did not reflect real-world behaviour (small set, likely near-duplicate images between train and validation, and bird photos often contain green backgrounds). I rebuilt the dataset with several different search queries per class and removed duplicate URLs: 233 images in total (187 train / 46 validation). Validation accuracy 97.8%; an informal test on new photos behaved correctly.
- **Caveats:** search results are noisy (some images may not be real login pages) and may contain duplicates or near-duplicates, which can leak between train and validation and inflate accuracy. Labels were not manually verified, so the 100% result should be read as "works on this small, noisy set", not as a reliable phishing detector.

## Week 2

- [x] Deploy the model as a live Gradio demo (Hugging Face Gradio Spaces now need a paid plan, so the demo runs from Colab through a Gradio share link)
- [x] Notes on attack types (malware, social engineering) from Professor Messer in `week2/notes.md`
- [x] TryHackMe: two more Pre-Security rooms

**Live demo (bird vs forest):** https://9aa153b422b55bad88.gradio.live/

> The link is temporary: it works only while the Colab notebook is running and Gradio share links expire after a while. The code to launch it again is `demo.launch(share=True)` (see `week2/space/app.py`).

## Structure

```
ai-cyber-lab/
├── notebooks/
│   └── 01_fastai_lesson1.ipynb
├── week1/
│   └── notes.md
├── week2/
│   ├── notes.md
│   └── space/            # files for the Hugging Face Space (app.py, requirements.txt, README.md)
├── requirements.txt
└── README.md
```

## Running on Colab

Open the notebook from GitHub in Colab (Runtime -> Change runtime type -> T4 GPU), then Run all.
