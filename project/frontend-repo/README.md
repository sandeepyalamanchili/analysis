# Dashboard — Frontend (deploy to Vercel)

This folder is its own Git repo. It contains only the dashboard page.

## Before you deploy
Open `index.html`, find this line near the top of the `<script>` section
(search for `BACKEND_BASE_URL`):

```js
const BACKEND_BASE_URL = '';
```

Once your backend is deployed on Render (see the `backend-repo` folder),
set this to your Render URL, no trailing slash:

```js
const BACKEND_BASE_URL = 'https://your-backend-name.onrender.com';
```

Leaving it blank is also fine — the dashboard still works, it just always
uses the slower in-browser parser instead of the Render backend.

## Push to GitHub via VS Code
1. Open this folder in VS Code.
2. Source Control tab → **Initialize Repository**.
3. Stage all files → commit (e.g. "initial commit").
4. **Publish Branch** → sign in to GitHub if prompted → this creates the
   remote repo and pushes it.

## Deploy on Vercel
1. vercel.com → sign in with GitHub.
2. **Add New → Project** → import this repo.
3. Leave settings as default → **Deploy**.
4. Vercel gives you a live URL like `https://your-app.vercel.app` — that's
   the link you share.

## After you have your final Vercel URL
Go back to the backend on Render and set its `ALLOWED_ORIGIN` environment
variable to this exact Vercel URL (see backend-repo/README.md), so only
your dashboard can talk to your backend.
