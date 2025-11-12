# Hybrid Fake News Detection (English & Hindi)

This folder contains a sanitized, GitHub-ready copy of the project notebook and helper files. The goal is to make this project safe to publish on GitHub by removing hard-coded API keys and providing clear setup instructions.

Contents
- `Fake_News_Detection_Hindi_English.ipynb` — The main Jupyter notebook (sanitized). It implements data collection (Twitter, RSS, News APIs), preprocessing, feature engineering (TF-IDF + social features), embeddings (SentenceTransformer), model training (RF, LR, LightGBM, MLP) and a stacked meta-model, evaluation and inference helpers.
- `.env.template` — Environment variable template containing placeholders for API keys. Copy to `.env` (do NOT commit `.env`).
- `.gitignore` — Recommended ignores to avoid committing large model files and secrets.

What changed
- Removed hard-coded API keys (Twitter, NewsAPI, GNews) from the notebook and replaced them with environment-variable lookups (os.getenv).
- Added `.env.template` so you can create a local `.env` file with your keys and keep secrets out of Git.
- Added `.gitignore` to prevent committing model artifacts and other large or sensitive files.

Project overview

This repository implements a hybrid fake-news detection system for English and Hindi. Main components:
- Data collection: Twitter collector (minimal 20 tweets), RSS feeds, optional NewsAPI/GNews integrations.
- Manual data collection helpers for WhatsApp/Facebook/Telegram-like examples.
- Preprocessing: multilingual text cleaning, language detection, deduplication.
- Augmentation: synthetic fake-news pattern generation to expand minority classes.
- Feature engineering: TF-IDF, statistical features, sentiment, social-media-specific features (emoji counts, urgency tokens), and SentenceTransformer embeddings (paraphrase-multilingual-MiniLM-L12-v2).
- Models: RandomForest, LogisticRegression, LightGBM, MLP (for embeddings), and a logistic regression meta-model for stacking.
- Inference: `FakeNewsDetector` and `ProductionFakeNewsDetector` classes that load saved artifacts and provide predict/predict_batch/explain functionality.

Security & privacy

- NEVER commit your `.env` or any file with API keys. Add keys to `.env` and keep it locally.
- `.gitignore` in this folder will prevent common large and secret files from being committed.

Quick start (local Jupyter)

1) Create a virtual environment and install dependencies (recommended):

   Windows (cmd.exe):

   ```
   python -m venv .venv
   .\.venv\Scripts\activate
   pip install -r requirements.txt
   ```

   Note: If `requirements.txt` is not present, install main packages used in the notebook (example):

   ```
   pip install transformers sentence-transformers datasets
   pip install lightgbm xgboost imbalanced-learn
   pip install vaderSentiment textblob langdetect
   pip install scikit-learn pandas numpy tqdm plotly kaleido
   pip install kagglehub tweepy emoji feedparser python-dotenv
   ```

2) Create a `.env` from `.env.template` and fill in your keys (DO NOT commit `.env`):

   - Copy `.env.template` to `.env`
   - Add values for TWITTER_API_KEY, TWITTER_API_SECRET, TWITTER_BEARER_TOKEN (if using Twitter), and NEWSAPI_KEY / GNEWS_KEY (optional)

3) (Optional) Use python-dotenv in the notebook to load `.env` automatically by adding at the top of the notebook (before keys are read):

   ```python
   from dotenv import load_dotenv
   load_dotenv()
   ```

4) Launch Jupyter and run the notebook cells in order. The notebook prints helpful messages when API keys are missing and skips API calls that require keys.

Notes for GitHub upload

- Keep the `Files` folder as the public entry point containing the sanitized notebook and README.
- If you plan to share model artifacts, provide a separate release or storage (GitHub Releases, Google Drive, or a model-hosting service) — avoid committing large models to the repo.

Next steps I can do for you
- Add a `requirements.txt` listing the exact packages used by the notebook.
- Add a small `run_env_loader.py` that loads `.env` and prints configured keys (sanity check).
- Create a `LICENSE` file and `CONTRIBUTING.md`.

If you'd like any of those, tell me which one and I'll add it.