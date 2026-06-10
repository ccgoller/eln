# Step 2 — Create a Template Repository

A template repository provides the starting folder structure, placeholder files, and instructions that every student notebook will be built from. Creating it once saves setup time for each student.

← **[Back to Instructor Setup](README.md)**

---

## 2.1 Create the Repository

1. Go to your organization page on GitHub.
2. Click **New repository**.
3. Fill in the details:
   - **Repository name:** `notebook-template`
   - **Description:** `Template for student ELN notebooks`
   - **Visibility:** **Private** (recommended — only organization members can see it)
4. Check **Add a README file**.
5. Click **Create repository**.

---

## 2.2 Mark It as a Template

1. In the new repository, go to **Settings → General**.
2. Under **Repository details**, check **Template repository**.
3. Click **Save changes**.

When you create student repositories in Step 3, you will use this template to pre-populate them.

---

## 2.3 Add the Recommended Folder Structure

Clone the template repository locally and set up the standard folder layout:

```bash
git clone https://github.com/your-org/notebook-template.git
cd notebook-template

# Create folders with placeholder files so Git tracks them
mkdir -p experiments data protocols references summaries
touch experiments/.gitkeep data/.gitkeep protocols/.gitkeep \
      references/.gitkeep summaries/.gitkeep

git add .
git commit -m "Initialize notebook folder structure"
git push
```

---

## 2.4 Add a Student README Template

Replace the auto-generated `README.md` with a student-facing template:

```markdown
# Lab Notebook — [Student Name]

**Course / Lab:** [Course or Lab Name]  
**Instructor:** [Instructor Name]  
**Term:** [Semester and Year]

---

## Project Overview

_Briefly describe your research question or project goals._

---

## Contents

| Folder | Description |
|--------|-------------|
| `experiments/` | Individual experiment entries |
| `data/` | Raw data files |
| `protocols/` | Step-by-step procedures |
| `references/` | Literature notes |
| `summaries/` | Weekly and milestone summaries |

---

## Recent Work

_Update this section weekly._
```

Commit this `README.md`:

```bash
git add README.md
git commit -m "Add student README template"
git push
```

---

## 2.5 Add Entry Templates

Copy the entry templates from this ELN repository into the template repository so students have them on day one:

```bash
mkdir -p templates
# Copy templates from the ELN guidelines repo
cp /path/to/eln/templates/experiment-entry.md templates/
cp /path/to/eln/templates/weekly-summary.md templates/

git add templates/
git commit -m "Add experiment entry and weekly summary templates"
git push
```

---

## 2.6 (Optional) Add a .gitignore

Add a `.gitignore` to prevent accidental commits of system files:

```gitignore
# macOS
.DS_Store

# Windows
Thumbs.db

# Jupyter Notebooks checkpoints
.ipynb_checkpoints/

# Python
__pycache__/
*.pyc
```

```bash
git add .gitignore
git commit -m "Add .gitignore"
git push
```

---

## Verification

Before continuing, confirm:

- [ ] The repository is visible at `github.com/your-org/notebook-template`.
- [ ] **Template repository** is checked in Settings.
- [ ] Folders `experiments/`, `data/`, `protocols/`, `references/`, `summaries/` exist.
- [ ] `templates/experiment-entry.md` and `templates/weekly-summary.md` are present.

---

## Next Step

→ [Invite Students](03-invite-students.md)
