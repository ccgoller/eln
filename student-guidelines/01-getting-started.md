# 1. Getting Started with GitHub

This guide takes you from zero to having a working lab notebook repository on GitHub.

← **[Back to Student Guidelines](README.md)**

---

## Step 1 — Create a GitHub Account

1. Go to [github.com](https://github.com) and click **Sign up**.
2. Choose a username that identifies you professionally (e.g., `firstname-lastname` or your university username).
3. Use your institutional email address if possible — this can qualify you for the [GitHub Student Developer Pack](https://education.github.com/pack).
4. Complete email verification.

---

## Step 2 — Enable Two-Factor Authentication (2FA)

Protecting your notebook with 2FA is required by most labs and courses.

1. Go to **Settings → Password and authentication**.
2. Under **Two-factor authentication**, click **Enable**.
3. Follow the prompts to set up an authenticator app (recommended) or SMS.

---

## Step 3 — Accept the Organization Invitation

Your instructor will send you an invitation to join the lab's GitHub Organization.

1. Check your email for an invitation from GitHub.
2. Click **Join** in the email, or go to [github.com/notifications](https://github.com/notifications) to find the invitation.
3. Accept the invitation. You should now see the organization listed on your GitHub profile.

---

## Step 4 — Find Your Notebook Repository

Your instructor will have created a notebook repository for you inside the organization.

1. Go to the organization page (your instructor will share the URL, e.g., `github.com/your-lab`).
2. Look for a repository named after you (e.g., `notebook-firstname-lastname`).
3. If you do not see one, notify your instructor.

---

## Step 5 — Install Git

You need Git on your computer to push changes from your local machine to GitHub.

### macOS
```bash
# Install Homebrew first if needed: https://brew.sh
brew install git
```

### Windows
Download Git from [git-scm.com/download/win](https://git-scm.com/download/win) and run the installer.

### Linux (Debian/Ubuntu)
```bash
sudo apt update && sudo apt install git
```

Verify the installation:
```bash
git --version
```

---

## Step 6 — Configure Git

Tell Git your name and email (use the same email as your GitHub account):

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

---

## Step 7 — Clone Your Notebook Repository

1. Navigate to your notebook repository on GitHub.
2. Click the green **Code** button and copy the HTTPS URL.
3. In your terminal, run:

```bash
git clone https://github.com/your-lab/notebook-your-name.git
cd notebook-your-name
```

Your notebook is now on your local computer. Any changes you make here can be pushed to GitHub.

---

## Step 8 — Make Your First Commit

Verify everything works by making a small change:

```bash
# Create today's first entry file
cp ../templates/experiment-entry.md experiments/YYYY-MM-DD_first-entry.md
# Edit the file, then save it

git add experiments/YYYY-MM-DD_first-entry.md
git commit -m "Add first experiment entry"
git push
```

Refresh the repository page on GitHub — you should see your new file.

---

## Next Step

→ [Structuring Your Lab Notebook](02-notebook-structure.md)
