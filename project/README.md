# Dashboard deployment — two repos

This is two *separate* Git repos in one folder, because the frontend and
backend deploy to two different services:

- `frontend-repo/` → push to its own GitHub repo → deploy on **Vercel**
- `backend-repo/`  → push to its own GitHub repo → deploy on **Render**

Read each folder's own README.md for exact steps. Suggested order:

1. Deploy `backend-repo` on Render first — you'll get a URL.
2. Paste that URL into `frontend-repo/index.html` (`BACKEND_BASE_URL`).
3. Deploy `frontend-repo` on Vercel — you'll get your public link.
4. Go back to Render and restrict `ALLOWED_ORIGIN` to that Vercel link.

Do NOT push this top-level folder itself to GitHub as one repo — open
and initialize `frontend-repo` and `backend-repo` separately in VS Code,
each as its own repo, each pushed to its own GitHub project.
