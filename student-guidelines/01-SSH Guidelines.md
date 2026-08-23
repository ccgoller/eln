# 1. Getting Started

The following guidelines explain how to clone your lab notebook to your computer. If you experienced problems with Enterprises when using GitHub and the HTTPS link, follow these guidelines: 

---

## Step 1: Getting an SSH key

1. Open the terminal on your computer
2. Copy and paste the following lines of code; make sure to replace the email address with your NCSU email: 

```bash
ssh-keygen -t ed25519 -C "youremail@example.com" 
```

This will create your SSH key. Is important you don't press any keys until prompted by the terminal. 

3. The terminal will prompt you for a location for the SSH key (the default location will work); press Enter.
4. The terminal will ask for a password and a password confirmation; press Enter for both.
5. If no error messages come through, it means your key was created! To retrieve your key, type the following command in the terminal:

```bash
cat ~/.ssh/id_ed25519.pub
```

6. Once you run this command, the terminal will give you an SSH key. **Copy all the output**; this is your key and you will need it for the next step.

## Step 2: Getting your key into GitHub

1. Open GitHub, click on your profile, and navigate to settings:
<img width="347" height="724" alt="Screenshot 2026-08-22 at 11 10 48 PM" src="https://github.com/user-attachments/assets/a327f91d-7a20-4817-895e-688f5859fd38" />



