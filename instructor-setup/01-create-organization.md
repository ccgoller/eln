# Step 1 — Create a GitHub Organization (optional)

A **GitHub Organization** is the shared workspace that houses all student notebook repositories. This keeps everything in one place and lets you manage access in bulk. GitHub offers limited free organization features. Your institution may support the creation of a GitHub Organization using your .edu account. Creation of a GitHub Organization is optional.

← **[Back to Instructor Setup](README.md)**

---

## 1.1 Create the Organization

1. Log in to GitHub with your instructor account.
2. Click the **+** icon in the top-right corner and select **New organization**.
3. Choose the **Free** plan (sufficient for most academic uses; see note below on GitHub Education).
4. Fill in the details:
   - **Organization name:** choose something short and identifiable, e.g., `goller-lab` or `mb360-fall2026`.
   - **Contact email:** your institutional email address.
   - **Belongs to:** select **My personal account** unless your institution has an enterprise account.
5. Click **Create organization**.

> **Tip — GitHub Education:** If you are using the organization for a course, apply for a [GitHub Education](https://education.github.com/teachers) discount. Verified educators receive free access to GitHub Team features (private repositories, etc.) for their organization.

<img width="2934" height="1600" alt="GitHub + button and 'Create a new organization' menu" src="/instructor-setup/GitHubOrganization.png" />

---

## 1.2 Configure Organization Settings

After creating the organization, adjust these settings (**Settings** tab of the organization):

### Member privileges
- **Base permissions:** set to **No permission** — students should only access repositories you explicitly grant them.
- **Allow members to create repositories:** **Disabled** — you will create notebook repositories for students.

### Repository defaults
- **Default branch name:** `main`

---

## 1.3 Add Yourself as an Owner

You are automatically an Owner when you create the organization. If you want a co-instructor or teaching assistant to also have admin access:

1. Go to **People** on the organization page.
2. Click **Invite member**.
3. Enter their GitHub username or email.
4. Set their role to **Owner**.

---

## 1.4 (Optional) Create Teams

Teams let you group students by lab section, project, or cohort and manage permissions at the group level.

1. Go to **Teams** on the organization page.
2. Click **New team**.
3. Name the team (e.g., `Team-Fungi`, `UGresearch-fall2026`).
4. Add members after you have invited them in Step 3.

---

## Verification

Before continuing, confirm:

- [ ] You can view the organization at `github.com/your-org-name`.
- [ ] You appear as an **Owner** under **People**.
- [ ] Member base permissions are set to **No permission**.

---

## Next Step

→ [Create a Template Repository](02-template-repository.md)
