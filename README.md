# Ascent 🏔️

A personal, Duolingo-style self-learning web app. Climb a path of 6 sequenced units covering engineering leadership, scaling teams, system design, architecture & reliability, tech strategy, and productivity habits.

Single self-contained `index.html`. No build step, no login, no backend. Your progress (XP, streak, completed lessons) is saved on your device with `localStorage`, so it survives closing the browser.

## Features

- **Learning path** of 6 units that unlock in order; each unit has 2 lessons of 3 multiple-choice questions (36 total).
- **Explanations** shown after every answer.
- **Game mechanics:** 3 hearts per lesson, +10 XP per correct answer, daily streak counter, and levels (100 XP per level).
- **Persistent progress** via `localStorage` — close Safari and pick up where you left off.
- **Mobile-first**, designed for iPhone Safari (safe-area aware, tap-friendly).

## Run it locally

It's a static file, so any of these work:

**Easiest — just open it:**
Double-click `index.html`, or in Terminal:
```bash
open index.html
```

**With a local server (recommended, behaves closest to hosting):**
```bash
cd ascent
python3 -m http.server 8000
```
Then visit **http://localhost:8000** in your browser.

### Preview on your iPhone (same Wi-Fi)
1. Run the server command above on your computer.
2. Find your computer's local IP (macOS: `ipconfig getifaddr en0`).
3. On your iPhone, open Safari to `http://<that-ip>:8000`.
4. Tap the Share icon → **Add to Home Screen** to use it like an app.

> Note: `localStorage` is tied to the specific browser/origin. Progress on your laptop and your iPhone are stored separately. Once deployed to a single URL (below), use that same URL everywhere and your progress stays consistent per device.

## Deploy to GitHub Pages

1. **Create a repo on GitHub** (e.g. `ascent`). Don't add a README there — you already have one.
2. **Push this folder:**
   ```bash
   cd ascent
   git remote add origin https://github.com/<your-username>/ascent.git
   git branch -M main
   git push -u origin main
   ```
3. **Turn on Pages:** in the repo, go to **Settings → Pages**. Under *Build and deployment*, set **Source: Deploy from a branch**, **Branch: `main`**, folder **`/ (root)`**, then **Save**.
4. Wait ~1 minute. Your app will be live at:
   ```
   https://<your-username>.github.io/ascent/
   ```
5. Open that URL on your iPhone and **Add to Home Screen**.

To update later, just commit and push — Pages redeploys automatically:
```bash
git add -A && git commit -m "Update lessons" && git push
```

## Reset progress

Tap **"Reset all progress"** at the bottom of the path screen, or clear the site's data in Safari settings.

## Customize

All lesson content lives in the `COURSE` array near the top of the `<script>` in `index.html`. Each question is `{ q, opts, a, e }` — question text, options array, index of the correct answer, and the explanation. Edit freely; the path, locking, XP, and levels all adapt automatically.
