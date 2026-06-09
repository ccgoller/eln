# Step 4 — Review and Grade Notebooks

This step covers how to check in on student progress, leave feedback, and assess lab notebook quality at the end of the term.

---

## 4.1 Protect the Main Branch (Optional but Recommended)

Requiring pull requests for changes to `main` creates a built-in review checkpoint. This is most useful in courses where formal notebook sign-offs are required.

1. In a student's repository, go to **Settings → Branches**.
2. Under **Branch protection rules**, click **Add rule**.
3. Set **Branch name pattern** to `main`.
4. Enable:
   - **Require a pull request before merging** (set "Required approvals" to 1 — you)
   - **Require status checks to pass** (if you have CI set up)
5. Click **Create** (or **Save changes**).

> **Note:** This means students must open a pull request and get your approval before merging significant updates. This is more overhead but provides a formal review trail. For low-overhead courses, skip this step and review commits directly.

---

## 4.2 Set Up Issue Labels

Consistent labels make it easy to track the type of feedback you leave across all notebooks.

Add these labels to each student repository (**Issues → Labels → New label**):

| Label | Color | Use |
|-------|-------|-----|
| `feedback` | `#0075ca` | General instructor comments |
| `missing-entry` | `#e4e669` | No entry for a scheduled lab session |
| `needs-revision` | `#d93f0b` | Entry requires correction or expansion |
| `approved` | `#0e8a16` | Entry reviewed and accepted |
| `question` | `#cc317c` | Student question for the instructor |

You can automate label creation with the GitHub CLI:

```bash
#!/usr/bin/env bash
ORG="your-org"
REPO="notebook-student-name"

gh label create "feedback"       --color "0075ca" --repo "$ORG/$REPO"
gh label create "missing-entry"  --color "e4e669" --repo "$ORG/$REPO"
gh label create "needs-revision" --color "d93f0b" --repo "$ORG/$REPO"
gh label create "approved"       --color "0e8a16" --repo "$ORG/$REPO"
gh label create "question"       --color "cc317c" --repo "$ORG/$REPO"
```

---

## 4.3 Reviewing Entries Week by Week

### Browsing commits

The most direct way to check a student's work is to view the commit history:

1. Go to the student's repository on GitHub.
2. Click **Commits** (the clock icon near the top of the file list).
3. Review commits since your last check-in, clicking each to see what changed.

Look for:
- At least one commit per lab session.
- Descriptive commit messages (not just "update").
- Data files added alongside entries.
- README updated with recent progress.

### Leaving inline comments on a commit

1. Open a commit (click its title in the commit list).
2. Hover over a line in the diff and click the **+** icon that appears.
3. Type your comment and click **Add single comment**.

The student will be notified by email.

### Leaving feedback via Issues

For broader feedback that is not tied to a specific line:

1. Go to the repository's **Issues** tab.
2. Click **New issue**.
3. Write your feedback and apply an appropriate label (e.g., `feedback`, `needs-revision`).
4. Assign the issue to the student so they receive a notification.

---

## 4.4 Assessing Notebooks at the End of the Term

### What to look for

Use a rubric adapted to your course. Common criteria:

| Criterion | Description |
|-----------|-------------|
| **Completeness** | Entry for every scheduled lab session |
| **Timeliness** | Commits made on or near the day of the experiment |
| **Detail** | Reagents, quantities, instrument settings recorded |
| **Data integrity** | Raw data files present and unmodified after initial commit |
| **Reflection** | Discussion and interpretation of results included |
| **Communication** | Clear writing; README kept up to date |
| **Version control** | Meaningful commit messages; commits throughout the process |

### Checking commit timestamps

Git commits include the author date. You can verify when work was actually committed:

```bash
git clone https://github.com/your-org/notebook-student-name.git
cd notebook-student-name
git log --pretty=format:"%h %ad %s" --date=short
```

GitHub also displays commit timestamps in the web interface.

### Downloading all notebooks for offline review

```bash
#!/usr/bin/env bash
ORG="your-org"

# Clone or pull all student notebooks into a local folder
mkdir -p student-notebooks
cd student-notebooks

gh repo list "$ORG" --limit 100 --json name \
  --jq '.[] | select(.name | startswith("notebook-")) | .name' \
| while read -r repo; do
    if [ -d "$repo" ]; then
      echo "Pulling $repo"
      git -C "$repo" pull
    else
      echo "Cloning $repo"
      gh repo clone "$ORG/$repo"
    fi
  done
```

---

## 4.5 End-of-Term Checklist

- [ ] All student repositories reviewed and feedback issues closed or resolved
- [ ] Grades recorded based on rubric
- [ ] Student access revoked or repositories archived (optional — see below)

### Archiving repositories

Archiving makes repositories read-only, preserving them as a permanent record without allowing further changes:

1. Go to the student's repository → **Settings → General → Danger Zone**.
2. Click **Archive this repository**.

Or via GitHub CLI (all student notebooks at once):

```bash
gh repo list your-org --limit 100 --json name \
  --jq '.[] | select(.name | startswith("notebook-")) | .name' \
| while read -r repo; do
    gh api \
      --method PATCH \
      -H "Accept: application/vnd.github+json" \
      "/repos/your-org/$repo" \
      -f archived=true
    echo "Archived $repo"
  done
```

---

## You're All Set

Your ELN system is fully operational. Refer to the [Student Guidelines](../student-guidelines/README.md) to share with students at the start of the term.
