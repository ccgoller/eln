# 1. Getting Started with GitHub

This guide helps you create a working lab notebook repository on GitHub.

← **[Back to Student Guidelines](README.md)**

---

## Step 1 — Create a GitHub Account

1. Go to [github.com](https://github.com) and click **Sign up**.
2. Choose a username that identifies you professionally (e.g., `firstname-lastname` or your university username).
3. Use your institutional email address — this can qualify you for the [GitHub Student Developer Pack](https://education.github.com/pack).
4. Complete the email verification step(s).

---

## Step 2 — Enable Two-Factor Authentication (2FA)

Enabling 2FA for your notebook is required by most labs and courses using GitHub Enterprise environments.

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

The notebook repository is available to all students; by creating your own fork, you ensure you have a "copy" of the notebook that you can then clone on your own computer. 

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
<img width="1285" height="462" alt="Screenshot 2026-08-13 at 2 02 24 PM" src="https://github.com/user-attachments/assets/43cb1ab4-0d28-4f00-90e0-569ebcf57f97" />
3. In your terminal, run:

```bash
git clone https://github.com/your-lab/notebook-your-name.git
```
Replace the link with the HTTPS URL you copied before. 

Your notebook is now on your local computer. Any changes you make here can be pushed to GitHub.

---

## Step 9 - Getting VS Code 

VS Code is an app that allows you to sync your GitHub repository (notebook) and be able to make changes to your notebook from your computer. 
1. Download VS Code from: https://code.visualstudio.com/download?_exp_download=fb315fc982 
2. Open the VS Code app, click the “Explorer” icon:
<img width="1241" height="945" alt="VS Code step 2" src="https://github.com/user-attachments/assets/8ecb8655-5322-4984-86c1-d17e3dee1d80" />
3. Click the “Open Folder” option and select the folder/ lab notebook you cloned to your computer in step 8. Your folder’s name is the one you chose in Step 5 (2).
<img width="1058" height="948" alt="VS Code step 3" src="https://github.com/user-attachments/assets/54b3bd92-e514-4470-bbe3-9400fdc88c2f" />
4. Once your folder has been selected, you can navigate through your lab notebook and make changes. Click on the “Notebooks” tab and navigate to Lab 1.

## Step 10 — Make Your First Commit

You have now opened Lab 1 from your Lab Notebook in VS Code and are ready to make changes. 
1. You can add anything in your notebook. Try to type something in the notebook. VS Code will show you the changes you are making to your notebook:
<img width="508" height="514" alt="Making your first commit - step1" src="https://github.com/user-attachments/assets/6385bb4a-4d41-4f64-b181-f7eb91b641a4" />

2. At the top of VS Code page, you can find the notebook that is currently open; a white dot next to it shows that there are unsaved changes: 
<img width="486" height="452" alt="Make your first commit - Step 2" src="https://github.com/user-attachments/assets/f6424657-17af-47ab-83de-fedff195ca1e" />

3. Press (Command + S for Mac) or (Ctrl + S in Windows) to save all changes. This will save changes in VS Code; however, extra steps are needed to commit and push a change so it shows in GitHub. 
4. Click on the “Fork” icon on the left side of the page: 
<img width="1052" height="543" alt="Make your first commit - Step 4" src="https://github.com/user-attachments/assets/5ebdc3ea-0c6f-4182-ab9c-9f833ced5534" />

5. Save the changes you want to commit. They will be shown by the name of the file (lab notebook) you just edited. Click the plus icon:  
<img width="303" height="203" alt="1st commit - step 5" src="https://github.com/user-attachments/assets/0fb6be3e-2b97-4ea8-b177-06737440d602" />

6. Click the drop-down menu and click the “Commit & Push” option. The commit option saves the changes on your computer, and the Push option saves the changes in your GitHub repository. 
<img width="459" height="282" alt="1st commit - step 6" src="https://github.com/user-attachments/assets/7fb3463d-cf76-476a-917e-1c98480e00ae" />

7. VS Code will prompt you to write a description of the changes you made. This helps you keep track of the changes you've made in the notebook. Feel free to add a small description and then click Commit:
<img width="482" height="872" alt="1st commit step 7" src="https://github.com/user-attachments/assets/2e099f3e-fdbd-4c20-b12e-efb67a78bc0b" />

---

## Next Step

→ [Structuring Your Lab Notebook](02-notebook-structure.md)
