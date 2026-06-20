# ❓ Frequently Asked Questions

Answers to common questions and troubleshooting tips for students and instructors using the GitHub-based Electronic Lab Notebook.

---

## Contents

- [General](#general)
- [GitHub Account and Access](#github-account-and-access)
- [Git Setup and Configuration](#git-setup-and-configuration)
- [Committing, Pushing, and Syncing](#committing-pushing-and-syncing)
- [Files and Data](#files-and-data)
- [Markdown and Formatting](#markdown-and-formatting)
- [Instructor Questions](#instructor-questions)

---

## General

### What is a GitHub-based ELN?

An Electronic Lab Notebook (ELN) built on GitHub stores your experimental records as plain-text Markdown files in a Git repository. Every change is tracked with a timestamp and author, making your notebook version-controlled, searchable, and auditable.

### Do I need to know how to code?

No. You only need to learn a handful of Git commands (`add`, `commit`, `push`, `pull`) and basic Markdown formatting. Both are covered in [Getting Started](student-guidelines/01-getting-started.md).

### Can I use GitHub Desktop instead of the command line?

Yes. [GitHub Desktop](https://desktop.github.com/) provides a graphical interface for all the core operations. The written guides use command-line examples, but every step has a Desktop equivalent.

### Can I use the GitHub web editor instead of cloning the repository?

For small edits, yes — click the pencil icon on any file in the GitHub web interface to edit it directly. For larger work (adding many files, uploading data), cloning to your computer is more practical.

---

## GitHub Account and Access

### I didn't receive the organization invitation email.

1. Check your spam or junk folder.
2. Log in to [github.com/notifications](https://github.com/notifications) to find the invitation directly.
3. If it has expired (invitations expire after 7 days), ask your instructor to re-send it.

### I accepted the invitation but I can't see my notebook repository.

- Make sure you are logged in to the correct GitHub account.
- Go to the organization page (your instructor will share the URL) and look under **Repositories**.
- If your repository is not there, notify your instructor — it may not have been created yet.

### My account was flagged or restricted by GitHub.

New accounts sometimes trigger GitHub's automated abuse-prevention checks. Open a support request at [support.github.com](https://support.github.com) with your institutional email and explain that you are a student. Resolution is usually quick.

---

## Git Setup and Configuration

### `git` is not recognized after installation (Windows).

Restart your terminal or open a new Command Prompt / PowerShell window after installing Git. If the problem persists, check that Git's `bin` directory is in your system `PATH` (the installer usually handles this automatically when you select "Git from the command line and also from 3rd-party software").

### Git is asking for my password on every push.

Configure a credential helper so Git remembers your credentials:

```bash
# macOS — use the system keychain
git config --global credential.helper osxkeychain

# Windows — use the built-in Windows Credential Manager
git config --global credential.helper manager

# Linux
git config --global credential.helper store
```

### I get "Please tell me who you are" when trying to commit.

Run the one-time configuration:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Use the same email address as your GitHub account.

### My commits show the wrong name or email.

Update your global config (see above). To fix the author on the most recent commit that has **not yet been pushed**:

```bash
git commit --amend --reset-author
```

Do not amend commits that have already been pushed — this rewrites history.

---

## Committing, Pushing, and Syncing

### `git push` asks for a username and password, but GitHub no longer accepts passwords.

GitHub removed password authentication for Git operations in August 2021. You need to authenticate with a **Personal Access Token (PAT)** or **SSH key**.

**Option A — Personal Access Token:**
1. Go to **GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)**.
2. Click **Generate new token**, select the `repo` scope, and set an expiry.
3. Copy the token. When Git prompts for a password, paste the token instead.

**Option B — SSH key:**
1. Generate a key: `ssh-keygen -t ed25519 -C "you@example.com"`
2. Add the public key to GitHub under **Settings → SSH and GPG keys**.
3. Change your remote URL to SSH: `git remote set-url origin git@github.com:your-lab/notebook-your-name.git`

### `git push` fails with "rejected — non-fast-forward".

Someone else pushed changes (or you pushed from another computer) after your last `git pull`. Sync first:

```bash
git pull --rebase
git push
```

### I committed to the wrong branch.

If the commit has not been pushed yet, you can move it:

```bash
# Create the correct branch at the current commit
git checkout -b correct-branch-name

# Remove the commit from the old branch (go back one commit)
git checkout wrong-branch-name
git reset --hard HEAD~1
```

### I accidentally committed a large file and push is failing.

GitHub rejects files larger than 100 MB. If the file was just committed (not yet pushed):

```bash
git rm --cached path/to/largefile
echo "path/to/largefile" >> .gitignore
git add .gitignore
git commit --amend --no-edit
```

For files larger than 50 MB, consider [Git LFS](https://git-lfs.com/).

### Changes I committed locally aren't showing on GitHub.

You have committed but not pushed. Run:

```bash
git push
```

Always push at the end of each session so your instructor can see your work.

---

## Files and Data

### What is the maximum file size I can commit?

GitHub warns for files over **50 MB** and blocks files over **100 MB**. For large data files (images, videos, raw instrument output), ask your instructor about enabling [Git LFS](https://git-lfs.com/) in your repository.

### My image isn't displaying in the Markdown file.

Check that:
1. The **relative path** in your Markdown matches the actual file location exactly (paths are case-sensitive on Linux/macOS).
2. The image file has been **committed and pushed** — a local file won't render on GitHub.
3. The file extension is supported (`.png`, `.jpg`, `.gif`, `.svg`, `.webp` all work).

```markdown
<!-- Example of a correct relative path from experiments/ to data/ -->
![Gel image showing two bands](../data/2025-03-14_gel-image.png)
```

### Can I store sensitive data (patient records, unpublished sequences) in the notebook?

**No**, if the repository is accessible to others. Consult your institution's data governance policies before committing any sensitive or regulated data. Use a **private** repository at a minimum, and consider whether GitHub's terms of service and your institution's policies permit the data type at all.

### How do I undo committing a file I shouldn't have committed?

If the file was just committed and **not yet pushed**:

```bash
git rm --cached sensitive-file.txt
echo "sensitive-file.txt" >> .gitignore
git add .gitignore
git commit --amend --no-edit
```

If it was already pushed, contact your instructor and consult [GitHub's documentation on removing sensitive data](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository).

---

## Markdown and Formatting

### My table isn't rendering correctly.

Tables in Markdown require:
- A header row.
- A separator row of dashes (`---`), one per column.
- `|` delimiters on each side.

```markdown
| Column A | Column B |
|----------|----------|
| value 1  | value 2  |
```

Make sure there are no extra blank lines inside the table.

### How do I add a checkbox (task list)?

```markdown
- [ ] Unchecked item
- [x] Checked item
```

Checkboxes render as interactive tick-boxes on GitHub.

### How do I write a code block?

Wrap code in triple backticks and optionally specify the language for syntax highlighting:

````markdown
```bash
git push
```

```python
import pandas as pd
```
````

### Headings in my file aren't appearing in the outline / table of contents.

Make sure there is a space between the `#` character and the heading text, and that the heading is not inside a code block:

```markdown
# Correct Heading

#IncorrectHeading
```

---

## Instructor Questions

### How many students can I add to a free GitHub Organization?

GitHub Free Organizations support unlimited members and unlimited public repositories. Private repositories are limited to **3 collaborators** per repo on the Free plan unless you are verified through [GitHub Education](https://education.github.com/teachers), which grants free Team-tier features.

### A student cannot see their repository.

1. Confirm the student accepted the organization invitation.
2. Go to the repository → **Settings → Collaborators and teams** and verify the student (or their team) has at least **Read** access.
3. If access was granted via a team, confirm the student is actually a member of that team.

### How do I leave feedback on a student's notebook?

Several options, depending on your preference:
- **GitHub Issues** — open an issue in the student's repository with your comments. This creates a persistent, dated record.
- **Pull Request reviews** — if students submit work via pull requests, use inline review comments.
- **Commit comments** — click on any commit in the repository and add a comment directly to that commit.

See [Review and Grade Notebooks](instructor-setup/04-review-notebooks.md) for a full workflow.

### Can I restrict students from editing their own commit history?

Enable **branch protection** on the `main` branch:
1. Go to **Settings → Branches → Add branch protection rule**.
2. Set branch name pattern to `main`.
3. Enable **"Require a pull request before merging"** and disable force-pushes.

This prevents `git push --force` and history rewrites on `main`.

### How do I bulk-create notebook repositories for all students?

Use the [GitHub Classroom](https://classroom.github.com/) tooling or the GitHub CLI with a simple shell loop:

```bash
# Requires gh CLI and appropriate org permissions
while IFS= read -r username; do
  gh repo create your-org/notebook-"$username" \
    --template your-org/notebook-template \
    --private \
    --add-collaborator "$username"
done < student-list.txt
```

See [Invite Students](instructor-setup/03-invite-students.md) for the full walkthrough.

---

## Still Stuck?

- Open a **GitHub Issue** in your notebook repository and tag your instructor.
- Consult the relevant section of the [Student Guidelines](student-guidelines/README.md) or [Instructor Setup Guide](instructor-setup/README.md).
- Visit [GitHub Docs](https://docs.github.com) for official documentation.
- Attend lab or course office hours.
