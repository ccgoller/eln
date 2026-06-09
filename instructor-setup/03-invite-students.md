# Step 3 — Invite Students

This step covers adding students to the GitHub Organization and creating an individual notebook repository for each of them.

---

## 3.1 Collect Student GitHub Usernames

Before inviting students, you need their GitHub usernames. Collect them via:

- A course survey or intake form (Google Form, etc.)
- A sign-up sheet during the first lab meeting

> Students who do not yet have a GitHub account should create one first. Point them to [Student Guidelines — Getting Started](../student-guidelines/01-getting-started.md).

---

## 3.2 Invite Students to the Organization

### Via the GitHub Web Interface (small cohorts)

1. Go to your organization page → **People** → **Invite member**.
2. Enter the student's GitHub username or email.
3. Set their role to **Member** (not Owner).
4. Click **Send invitation**.

The student will receive an email and must accept the invitation within 7 days.

### Via GitHub CLI (large cohorts)

If you have many students, use the [GitHub CLI](https://cli.github.com/) to automate invitations. Save usernames in a plain text file, one per line (`students.txt`):

```bash
# Authenticate first
gh auth login

# Invite all students
while IFS= read -r username; do
  gh api \
    --method PUT \
    -H "Accept: application/vnd.github+json" \
    "/orgs/your-org/memberships/$username" \
    -f role=member
  echo "Invited $username"
done < students.txt
```

---

## 3.3 Create Individual Notebook Repositories

Each student gets their own private repository generated from the template.

### Via the GitHub Web Interface

1. Go to your organization → **New repository**.
2. Under **Repository template**, select `notebook-template`.
3. Name the repository: `notebook-firstname-lastname` (use the student's actual name).
4. Set visibility to **Private**.
5. Click **Create repository**.
6. Repeat for each student.

### Via GitHub CLI (recommended for large cohorts)

Save student names and usernames in a CSV file (`students.csv`):

```
firstname,lastname,github_username
Jane,Smith,janesmith
John,Doe,johndoe
```

Run the following script:

```bash
#!/usr/bin/env bash
ORG="your-org"
TEMPLATE="notebook-template"

tail -n +2 students.csv | while IFS=',' read -r first last username; do
  REPO="notebook-${first,,}-${last,,}"   # lowercase names

  # Create repo from template
  gh repo create "$ORG/$REPO" \
    --template "$ORG/$TEMPLATE" \
    --private

  # Grant the student write access to their own repo
  gh api \
    --method PUT \
    -H "Accept: application/vnd.github+json" \
    "/repos/$ORG/$REPO/collaborators/$username" \
    -f permission=push

  echo "Created $REPO and added $username"
done
```

> **Permission level:** `push` (write) lets students commit and push. Use `triage` if you want students to only open issues.

---

## 3.4 Share Repository Links with Students

Once repositories are created, share the direct link with each student:

```
https://github.com/your-org/notebook-firstname-lastname
```

Remind students to:
1. Accept the organization invitation from their email.
2. Clone their repository following [Student Guidelines — Getting Started](../student-guidelines/01-getting-started.md), Step 7.

---

## 3.5 (Optional) Add Students to a Team

If you created Teams in Step 1, add students now:

1. Go to **Teams** → select the team → **Add a member**.
2. Enter the student's username.

You can also use the GitHub CLI:

```bash
gh api \
  --method PUT \
  -H "Accept: application/vnd.github+json" \
  "/orgs/your-org/teams/your-team/memberships/student-username" \
  -f role=member
```

---

## Verification

Before continuing, confirm:

- [ ] All students have received and accepted their organization invitation.
- [ ] Each student has a private repository under `github.com/your-org/notebook-...`.
- [ ] Each student has `push` (write) access to their own repository.
- [ ] Students can clone and push to their repositories (ask them to verify).

---

## Next Step

→ [Review and Grade Notebooks](04-review-notebooks.md)
