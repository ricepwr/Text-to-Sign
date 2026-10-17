# ASL-to-Text Computer Vision Project

A computer vision model that watches a person signing American Sign Language (ASL) through a webcam and outputs plain English text.

## Scope (tiers)

1. **Isolated signs:** classify one signed word at a time from a fixed vocabulary (about 100 signs to start).
2. **Fingerspelling:** read spelled-out letters into words, names, and numbers.
3. **Continuous sentences:** stretch goal.

## How it works

Webcam or video → MediaPipe landmarks (keypoints for hands, body, face) → normalize and window → sequence model (LSTM first) → text output.

## Folder layout

```
asl-to-text/
├── README.md          this file
├── RESULTS.md         experiment log (one row per experiment)
├── requirements.txt   Python packages
├── .gitignore         files Git should not track
├── src/               reusable code (.py files)
├── notebooks/         exploration and experiments (.ipynb)
└── data/              datasets and models (NOT tracked by Git; created locally)
```

Create `src/`, `notebooks/`, and `data/` locally as needed. Git does not track empty folders, so each appears in the repository once it contains a file.

## Setup

Python 3.10 or 3.11 is recommended, since MediaPipe works best with Python 3.9 to 3.11.

```bash
# 1. Clone the repository (or use GitHub Desktop: File > Clone repository)
git clone https://github.com/<username>/asl-to-text.git
cd asl-to-text

# 2. Create and activate a virtual environment
python -m venv .venv
# Windows:   .venv\Scripts\activate
# Mac/Linux: source .venv/bin/activate

# 3. Install packages
pip install -r requirements.txt
```

Open `requirements.txt` and choose either TensorFlow or PyTorch (one framework for the whole project) before installing.

## Data

Datasets and trained models are large and are **never committed to Git**. Each person downloads them locally into `data/`. Add the download steps for each dataset used below.

| Dataset | Used for | How to get it |
| --- | --- | --- |
| WLASL (100-sign subset) | Tier 1 | https://github.com/dxli94/WLASL |
| ASL Citizen | Tier 1 | https://www.microsoft.com/en-us/research/project/asl-citizen/dataset-description/ |
| Google ASL Fingerspelling | Tier 2 | https://www.kaggle.com/competitions/asl-fingerspelling/overview |

Check each dataset's license and access terms before downloading.

## Working together

- Pull the latest changes before starting work.
- Work on a branch and merge through a pull request.
- Commit small and often, with a plain message.
- Log every experiment in `RESULTS.md`.
- Never commit data, videos, trained models, passwords, or API keys.
