# Dashboard — Backend (deploy to Render)

This folder is its own Git repo. It contains only the fast Excel-parsing
API — no dashboard page here, that lives in `frontend-repo` on Vercel.

## Push to GitHub via VS Code
1. Open this folder in VS Code.
2. Source Control tab → **Initialize Repository**.
3. Stage all files → commit (e.g. "initial commit").
4. **Publish Branch** → sign in to GitHub if prompted → this creates the
   remote repo and pushes it.

## Deploy on Render
1. render.com → sign in with GitHub.
2. **New → Web Service** → connect this repo.
   (Render will read `render.yaml` automatically and pre-fill the settings
   below — you can skip straight to "Create Web Service" if it detects it.)
3. If asked manually, confirm:
   - Build command: `pip install -r requirements.txt`
   - Start command: `python server.py`
4. **Create Web Service**. First deploy takes a few minutes.
5. Copy the URL Render gives you, e.g.
   `https://dashboard-backend-xxxx.onrender.com`
   — paste this into `frontend-repo/index.html`'s `BACKEND_BASE_URL`
   (see that repo's README), then commit + push the frontend again.

Note: on Render's free tier this service sleeps after inactivity and
takes ~30-50 seconds to wake up on the next request — that's normal,
not a bug.

## Lock it down (recommended once everything works)
By default `ALLOWED_ORIGIN` is `*`, meaning any website can call this
backend. Once you have your final Vercel URL:
1. Render dashboard → this service → **Environment**.
2. Add variable: `ALLOWED_ORIGIN` = your exact Vercel URL
   (e.g. `https://your-app.vercel.app`, no trailing slash).
3. Render redeploys automatically with the new setting.
