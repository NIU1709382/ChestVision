# ChestVision

AI and Visualization UE, 2026. We investigate how a chest X-ray classifier behaves across patient and acquisition subgroups, then test selected hypotheses with controlled image changes.

Repository: https://github.com/Patrik835/ChestVision

## Task, model, and data

- **Task:** link image metadata with prediction scores, false positives, and false negatives in an interactive visualization. Compare sex, age, AP/PA view, and support-device groups.
- **Model:** TorchXRayVision `densenet121-res224-all`, a pretrained multi-label chest X-ray classifier. Its training sources include CheXpert; this is exploratory model analysis, not an independent generalization benchmark.
- **Dataset:** [CheXpert](https://stanfordmlgroup.github.io/competitions/chexpert/), accessed through the [Kaggle mirror](https://www.kaggle.com/datasets/ashery/chexpert). The initial notebook uses frontal images: 5,000 training images sampled with seed 42 plus the available frontal validation images (5,202 total in the run).
- **Hypotheses:** subgroup error differences may relate to acquisition view, age, support devices, or label imbalance. Paired perturbations will test sensitivity to borders/text markers, flips, brightness/contrast, and regions outside the lungs.

The existing [Phase I notebook](aivis.ipynb) contains exploratory analysis and a border masking pilot.

## Run the notebook

Use the **Open in Colab** link in [aivis.ipynb](aivis.ipynb), or run locally with Python 3.11+:

```sh
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter lab aivis.ipynb
```

Run all cells in order. A GPU is recommended; inference falls back to CPU. The first cells install notebook dependencies, download `ashery/chexpert` with KaggleHub, and download the pretrained model weights. Dataset access may require Kaggle authentication and acceptance of its terms.


## Repository guide

| Path | Purpose |
| --- | --- |
| `team-info.json` | Team details; empty strings are unfilled member slots |
| `workload.json` | Current reported contribution |
| `aivis.ipynb` | Phase I analysis and border-masking pilot |
| `phase-1/README.md` | Existing results and limits |
| `phase-2/README.md` | Final submission preparation  |
| `ai-interactions/phase-1.md`, `ai-interactions/phase-2.md` | Phase I and Phase II AI interaction records |
| `genai-reflection.md` | GenAI reflection |
