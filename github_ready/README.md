# Fake News Detection (GitHub-ready)

This folder contains a sanitized, GitHub-ready copy of the project notebook and helper files.

Contents
- `Fake_News_Detection_Hindi_English.ipynb` — Sanitized notebook with hard-coded API keys removed.
- `.env.template` — Template showing which API keys and environment variables to provide.
- `.gitignore` — Recommended ignores for sensitive artifacts and large model files.

What I changed
- Removed hard-coded API keys (Twitter, NewsAPI, GNews) from the notebook and replaced them with environment-variable lookups (os.getenv).
- Added `.env.template` so you can create a `.env` file locally with your keys.
- Added `.gitignore` to prevent committing secrets and large model artifacts.

How to use
1. Copy the sanitized notebook into your repository (already included here).
2. Create a `.env` file at the project root (NOT committed) using `.env.template` as a guide. Example contents:

   TWITTER_API_KEY=your_twitter_api_key_here
   TWITTER_API_SECRET=your_twitter_api_secret_here
   TWITTER_BEARER_TOKEN=your_twitter_bearer_token_here
   NEWSAPI_KEY=your_newsapi_key_here
   GNEWS_KEY=your_gnews_key_here

3. (Optional) If using a local Jupyter environment, you can load env vars before launching Jupyter:

   - Windows (cmd.exe):
     set TWITTER_API_KEY=...
     set TWITTER_API_SECRET=...
     set TWITTER_BEARER_TOKEN=...
     set NEWSAPI_KEY=...
     set GNEWS_KEY=...
     jupyter notebook

   - Or use a `.env` loader like `python-dotenv` in the notebook.

4. Run the notebook cells. If any API key is missing the notebook prints a clear message and skips calls that require keys.

Notes
- Do NOT commit `.env` containing real keys. Keep secrets out of Git history.
- The notebook still contains code that saves trained models to `/content/models/` — consider ignoring or removing those artifacts before pushing large files.

If you'd like, I can now attempt to push these files into your GitHub repo (will require authentication).