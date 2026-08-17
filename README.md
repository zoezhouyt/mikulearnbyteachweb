# Miku — Learning by teaching

A single-page marketing/research site for Miku, an experimental learning environment where a learner teaches a "faithfully ignorant" AI pupil and then predicts how well it will perform on a quiz.

Static site — no build step. `index.html` plus `assets/`.

## Deploy on Vercel

1. Push this repo to GitHub.
2. In Vercel, "Add New… → Project" and import the repo.
3. Framework preset: **Other** (static). No build command, no output directory override needed — Vercel serves `index.html` from the repo root as-is.
4. Deploy.

## Local preview

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.
