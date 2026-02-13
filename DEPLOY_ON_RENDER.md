# 🚀 Deploying Hinata Bot to Render

Follow these exact steps to host your bot on Render for free (or paid):

### 1. Prepare your Repository

- Ensure your bot folder has these files:
  - `bot.py` (Main logic)
  - `requirements.txt` (Dependencies)
  - `Procfile` (Starts the worker)
  - `runtime.txt` (Fixes Python version)
  - `token.txt` (Contains your Bot Token)
- Upload everything to a **Private GitHub Repository**.

### 2. Create a Web Service on Render

- Log in to [Render.com](https://render.com).
- Click **New** > **Background Worker** (or Web Service if using a webhook, but Worker is better for polling).
- Connect your GitHub repository.

### 3. Settings

- **Region:** Choose the one closest to you (e.g., Singapore or US East).
- **Branch:** `main` (or yours).
- **Runtime:** `Python 3`.
- **Build Command:** `pip install -r requirements.txt`.
- **Start Command:** `python bot.py`.

### 4. Important: Environment & Files

- If you don't want to upload `token.txt` to GitHub, you can add an **Environment Variable** on Render:
  - Key: `BOT_TOKEN`
  - Value: `Your_Token_Here`
- (Note: The current `bot.py` looks for `token.txt`. You can modify it to use `os.environ` if needed).

### 5. Deployment

- Click **Create Background Worker**.
- Wait for the build to finish. Once it says "Hinata Live" in the logs, you're good to go!

---

✨ **Pro Tip:** For 24/7 uptime on Free Tier, use a "simple ping" service like Cron-job.org to hit your bot's URL (if you converted to a Web Service) or just upgrade to a basic instance.
