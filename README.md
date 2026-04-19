# EUmove — Demo

A single-page, client-only React prototype of **EUmove**, an AI-assisted cross-border migration companion for EU citizens. This demo follows a sample user (Sophie van der Berg) moving from the Netherlands to Germany, and shows personalised tasks, opportunities, a profile, and an assistant chat.

The whole app lives inside `index.html`:

- React 18 + Babel Standalone via CDN (no build step)
- Fraunces + Inter web fonts
- All state is in-memory (ticks, notes, and profile edits are lost on refresh — by design, no backend)

## Run locally

Just open `index.html` in a browser. Or serve it with any static file server:

```bash
npx serve .
# or
python3 -m http.server 8000
```

Then visit http://localhost:8000.

## Deploy to Vercel (free)

### Option A — Vercel CLI (fastest)

```bash
npm i -g vercel
vercel            # first deploy (preview)
vercel --prod     # production deploy
```

Accept the defaults. Vercel auto-detects it as a static site; no framework preset needed.

### Option B — GitHub + Vercel dashboard

1. Create a new repository on GitHub and push this folder:
   ```bash
   git remote add origin https://github.com/<your-user>/eumove-demo.git
   git push -u origin main
   ```
2. Go to [vercel.com/new](https://vercel.com/new) and import the repo.
3. Leave all build settings empty (it's a pure static site).
4. Click **Deploy**. Vercel gives you a free `*.vercel.app` URL.

Subsequent pushes to `main` auto-deploy.

### Option C — Drag & drop

Go to [vercel.com/new](https://vercel.com/new), pick **"Deploy a template / upload a folder"**, and drop this folder.

## What's inside

```
.
├── index.html       # entire app (React via CDN)
├── vercel.json      # static-site routing config
├── .gitignore
└── README.md
```

## Notes / known limitations

This is a demo, so:

- No persistence — refreshing resets completed tasks, notes, and profile edits.
- The Profile "Save changes" button is cosmetic; fields already update live.
- The assistant has 4 canned answers plus a generic fallback (see the `AI` object in `index.html`).
- `departureDate` and `daysLeft` aren't linked; the "19 days" count is hard-coded.

If this prototype graduates to a real product, the natural next steps would be:
a small backend or edge KV for persistence, real EUDIW integration, and a proper markdown renderer for assistant answers.
