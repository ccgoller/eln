# 1. Getting Started with GitHub

This guide helps you have a working lab notebook repository on GitHub.

← **[Back to Student Guidelines](README.md)**

---

## Step 1 — Create a GitHub Account

1. Go to [github.com](https://github.com) and click **Sign up**.
2. Choose a username that identifies you professionally (e.g., `firstname-lastname` or your university username).
3. Use your institutional email address — this can qualify you for the [GitHub Student Developer Pack](https://education.github.com/pack).
4. Complete the email verification step(s).

---

## Step 2 — Enable Two-Factor Authentication (2FA)

Enabling 2FA for your notebook is required by most labs and courses.

1. Go to **Settings → Password and authentication**.
2. Under **Two-factor authentication**, click **Enable**.
3. Follow the prompts to set up an authenticator app (recommended) or SMS.

---

## Step 3 — Accept the Organization Invitation

Your instructor will send you an invitation to join the lab's GitHub Organization.

1. Check your email for an invitation from GitHub.
2. Click **Join** in the email, or go to [github.com/notifications](https://github.com/notifications) to find the invitation.
3. Accept the invitation. If applicable, you should now see the organization listed on your GitHub profile.

---

## Step 4 — Find Your Notebook Repository

Your instructor will have created a notebook repository for you, sometimes inside a "GitHub organization."

1. Go to the organization page (your instructor will share the URL, e.g., `github.com/your-lab`).
2. Look for your course repository.
3. If you do not see one, notify your instructor.

---

## Step 5 — Fork Main Repository

The notebook repository is available to all students; by creating your own fork, you ensure you have a "copy" of the notebook which can then be cloned in your own computer. 

1. In the upper-right corner, there is an option to fork a repository; select it. 
<img width="1306" height="743" alt="Fork" src="https://github.com/user-attachments/assets/286449e8-83ee-41e0-8b08-c9881a53c68e" />
2. In the "Choose Owner" drop-down menu, choose your name. In the “Repository Name” tab, type: mb360-Your Name
<img width="796" height="499" alt="Screenshot 2026-08-12 at 11 31 25 AM" src="https://github.com/user-attachments/assets/07feb178-7cc2-44bc-9140-df5dfc860621" />

You have forked the main repository, which means you have a “copy” of the main repository where you can push changes and update from the main branch if necessary. 

---

## Step 6 — Install Git

You need Git on your computer to push changes from your local machine to GitHub. Open the terminal app on your computer and run the following lines of code depending on your operating system (macOS, Windows, or Linux)  

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

## Step 7 — Configure Git

Tell Git your name and email (use the same email as your GitHub account):

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

---

## Step 8 — Clone Your Notebook Repository

1. Navigate to your notebook repository on GitHub.
2. Click the green **Code** button and copy the HTTPS URL.
3. In your terminal, run:

```bash
git clone https://github.com/your-lab/notebook-your-name.git
cd notebook-your-name
```

Your notebook is now on your local computer. Any changes you make here can be pushed to GitHub.

---

## Step 9 — Make Your First Commit

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
