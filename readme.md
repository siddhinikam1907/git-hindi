# Learn from chai aur code

🔐 SSH Key Setup for GitHub – Step-by-Step
✅ 1. Generate a New SSH Key
Open Git Bash and run:
bash
Copy code
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
Replace "your_email@example.com" with your GitHub email.
When prompted:
• Press Enter to accept the default file location: ~/.ssh/id_rsa
• Optionally enter a passphrase (or leave it empty and press Enter)

---

✅ 2. Start the SSH Agent
bash
Copy code
eval "$(ssh-agent -s)"
This starts the background service that manages your keys.

---

✅ 3. Add Your Private Key to the Agent
bash
Copy code
ssh-add ~/.ssh/id_rsa
If your key has a custom name (e.g., id_ed25519):
bash
Copy code
ssh-add ~/.ssh/id_ed25519

---

✅ 4. Copy Your Public Key to Clipboard
bash
Copy code
cat ~/.ssh/id_rsa.pub
Copy the entire output (starts with ssh-rsa or ssh-ed25519) manually.

---

✅ 5. Add the Public Key to GitHub

1. Go to GitHub > Settings > SSH and GPG keys
2. Click "New SSH key"
3. Give a title like "My Laptop Key"
4. Paste your copied public key into the Key field
5. Click "Add SSH key"

---

✅ 6. Test Your Connection
bash
Copy code
ssh -T git@github.com
If successful, you'll see:
vbnet
Copy code
Hi your-username! You've successfully authenticated, but GitHub does not provide shell access.

---

✅ 7. (Optional) Verify Keys in Agent
bash
Copy code
ssh-add -l
You should see something like:
bash
Copy code
2048 SHA256:abc123... /c/Users/HP/.ssh/id_rsa (RSA)

---

✅ 8. Use the SSH URL to Clone Repos
Use the SSH link (instead of HTTPS) when cloning:
bash
Copy code
git clone git@github.com:your-username/your-repo.git
