# ai-cyber-lab

معمل عملي بيجمع بين الـ Machine Learning والأمن السيبراني. كل أسبوع له notebooks وملاحظات ونتايج.

## Roadmap

| Week | Topic | Status |
|------|-------|--------|
| 1 | Setup + أول مصنف صور (fast.ai Lesson 1) + TryHackMe Pre-Security | In progress |

## Week 1

- [x] إنشاء الـ repo وتجهيز Colab
- [ ] تشغيل notebook الدرس 1 زي ما هو
- [ ] تدريب مصنف على حاجتين من اختياري
- [ ] TryHackMe: أول 3 غرف Pre-Security

### Results

| Experiment | Classes | Images per class | Model | Accuracy |
|-----------|---------|------------------|-------|----------|
| Lesson 1 baseline (bird vs forest) | 2 | ~200 | resnet18 | _TBD_ |
| Custom classifier | _TBD_ | _TBD_ | resnet18 | _TBD_ |

### Data collection notes

_اكتب هنا الصور جت منين، عددها، وأي تنضيف عملته._

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

افتح الـ notebook من GitHub في Colab، فعّل T4 GPU من `Runtime → Change runtime type`، وبعدين Run all.
