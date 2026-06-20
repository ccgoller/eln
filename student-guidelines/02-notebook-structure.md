# 2. Structuring Your Lab Notebook

A consistent folder structure makes your notebook easy to navigate — for you, your collaborators, and your instructor.

← **[Back to Student Guidelines](README.md)**

---

## Recommended Folder Layout

```
notebook-your-name/
├── README.md                  ← overview and project summary (update regularly)
├── experiments/               ← one file per experiment or session
│   ├── YYYY-MM-DD_title.md
│   └── ...
├── data/                      ← raw data files (CSV, images, etc.)
│   ├── YYYY-MM-DD_dataset.csv
│   └── ...
├── protocols/                 ← reusable step-by-step procedures
│   └── protocol-name.md
├── references/                ← papers, notes, and literature summaries
│   └── author-YYYY-keyword.md
└── summaries/                 ← weekly or milestone summaries
    └── YYYY-WXX_weekly.md
```

---

## File Naming Conventions

| Folder | Pattern | Example |
|--------|---------|---------|
| `experiments/` | `YYYY-MM-DD_short-title.md` | `2025-03-14_pcr-optimization.md` |
| `data/` | `YYYY-MM-DD_description.ext` | `2025-03-14_gel-image.png` |
| `protocols/` | `protocol-name.md` | `protocol-western-blot.md` |
| `references/` | `author-YYYY-keyword.md` | `smith-2022-crispr.md` |
| `summaries/` | `YYYY-WXX_weekly.md` | `2025-W11_weekly.md` |

**Rules:**
- Use **lowercase** and **hyphens** instead of spaces.
- Always start experiment and data files with the **ISO date** (`YYYY-MM-DD`) for automatic chronological sorting.
- Keep titles short but descriptive.

---

## Your README.md

Your repository's `README.md` is the front page of your notebook. Keep it updated with:

- **Project title and brief description**
- **Your name and contact / institutional affiliation**
- **Objectives** — what are you trying to find out?
- **Status** — what stage is the project at?
- **Index of major experiments** (optional, link to key entries)

---

## Setting Up the Structure

Run these commands once after cloning your repository:

```bash
cd notebook-your-name

mkdir -p experiments data protocols references summaries

# Create placeholder files so Git tracks the empty folders
touch experiments/.gitkeep data/.gitkeep protocols/.gitkeep \
      references/.gitkeep summaries/.gitkeep

git add .
git commit -m "Initialize notebook folder structure"
git push
```

---

## Next Step

→ [Recording Experiments](03-recording-experiments.md)
