# 🔒 Setting up SSH Keys with GitHub

<div align="center">
  <i>A step-by-step guide to securely connect your local repository to GitHub</i>
</div>

---

## 📋 Table of Contents
- [Prerequisites](#prerequisites)
- [Step 1: Check for Existing SSH Keys](#step-1-check-for-existing-ssh-keys)
- [Step 2: Generate New SSH Key](#step-2-generate-new-ssh-key)
- [Step 3: Copy Your Public Key](#step-3-copy-your-public-key)
- [Step 4: Add SSH Key to GitHub](#step-4-add-ssh-key-to-github)
- [Step 5: Test SSH Connection](#step-5-test-ssh-connection)
- [Step 6: Update Repository Remote URL](#step-6-update-repository-remote-url)
- [Optional: Set Up SSH Agent](#optional-set-up-ssh-agent-recommended)
- [Troubleshooting](#troubleshooting)
- [SSH Key Security Best Practices](#ssh-key-security-best-practices)
- [Notes](#notes)

---

## 🛠️ Prerequisites

| Requirement | Description |
|-------------|-------------|
| Git | Version control software installed on your machine |
| Terminal | WSL (Windows Subsystem for Linux), Linux terminal, or Windows PowerShell |
| GitHub Account | Active account on GitHub.com |

---

## 🔍 Step 1: Check for Existing SSH Keys

### Linux/WSL:
```bash
ls -la ~/.ssh
```

### Windows PowerShell:
```powershell
dir C:\Users\$env:USERNAME\.ssh
```

If you see files like `id_ed25519` or `id_rsa`, you already have SSH keys. You have two options:

### Option A: Use Existing Key
If you want to use your existing key, you can skip to [Step 3](#step-3-copy-your-public-key) to copy and add it to GitHub.

### Option B: Create New Key
If you want to create a new key instead:

#### Linux/WSL:
1. Back up your existing key (optional but recommended):
   ```bash
   mv ~/.ssh/id_ed25519 ~/.ssh/id_ed25519.backup
   mv ~/.ssh/id_ed25519.pub ~/.ssh/id_ed25519.pub.backup
   ```
2. Continue with Step 2 to generate a new key

#### Windows PowerShell:
1. Back up your existing key (optional but recommended):
   ```powershell
   Move-Item C:\Users\$env:USERNAME\.ssh\id_ed25519 C:\Users\$env:USERNAME\.ssh\id_ed25519.backup
   Move-Item C:\Users\$env:USERNAME\.ssh\id_ed25519.pub C:\Users\$env:USERNAME\.ssh\id_ed25519.pub.backup
   ```
2. Continue with Step 2 to generate a new key

> **About SSH Key Types**: We use `ed25519` because it's currently the most secure and efficient SSH key type available. It's faster than RSA keys, more secure (resistant to quantum computer attacks), has shorter key length while maintaining high security, and is recommended by GitHub and other major platforms. The older RSA key type (which you might see as `id_rsa`) is still widely used but is gradually being phased out in favor of ed25519.

---

## 🔐 Step 2: Generate New SSH Key

### Linux/WSL:
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

### Windows PowerShell:
```powershell
ssh-keygen -t ed25519 -C "your_email@example.com"
```

| Prompt | Recommendation |
|--------|----------------|
| File location | Press Enter to accept the default (`/home/your_username/.ssh/id_ed25519` on Linux/WSL or `C:\Users\username\.ssh\id_ed25519` on Windows) |
| Passphrase | Setting a passphrase is recommended for security, or press Enter twice for no passphrase (less secure but more convenient) |

---

## 📋 Step 3: Copy Your Public Key

### Linux/WSL:
```bash
cat ~/.ssh/id_ed25519.pub
```

### Windows PowerShell:
```powershell
type C:\Users\$env:USERNAME\.ssh\id_ed25519.pub
```

Copy the entire output (starts with `ssh-ed25519` and ends with your email)

---

## 🌐 Step 4: Add SSH Key to GitHub

| Step | Action |
|------|--------|
| 1 | Go to GitHub.com → Settings |
| 2 | Click "SSH and GPG keys" in the left sidebar |
| 3 | Click "New SSH key" |
| 4 | Give it a title (e.g., "WSL Ubuntu") |
| 5 | Paste your public key |
| 6 | Click "Add SSH key" |

---

## ✅ Step 5: Test SSH Connection

### Linux/WSL:
```bash
ssh -T git@github.com
```

### Windows PowerShell:
```powershell
ssh -T git@github.com
```

You should see: "Hi username! You've successfully authenticated, but GitHub does not provide shell access."

---

## 🔄 Step 6: Update Repository Remote URL

If you have an existing repository using HTTPS, update it to use SSH:

### Linux/WSL:
```bash
git remote set-url origin git@github.com:username/repository.git
```

### Windows PowerShell:
```powershell
git remote set-url origin git@github.com:username/repository.git
```

---

## 🔧 Optional: Set Up SSH Agent (Recommended)

To avoid entering your passphrase repeatedly, you can set up the SSH agent:

### Linux/WSL:
1. Start the SSH agent:
   ```bash
   eval "$(ssh-agent -s)"
   ```

2. Add your SSH key to the agent:
   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

3. Enter your passphrase once when prompted

### Windows PowerShell:
1. Start the SSH agent:
   ```powershell
   Start-Service ssh-agent
   ```

2. Add your SSH key to the agent:
   ```powershell
   ssh-add C:\Users\$env:USERNAME\.ssh\id_ed25519
   ```

3. Enter your passphrase once when prompted

---

## 🛡️ SSH Key Security Best Practices

### File Permissions

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_ed25519
chmod 644 ~/.ssh/id_ed25519.pub
```

This ensures only you can read/write your private key.

### Backup Strategy

| Action | Best Practice |
|--------|---------------|
| Backup Location | Keep a secure backup of your private key (`id_ed25519`) |
| Storage | Store backups in an encrypted location (password manager, encrypted drive) |
| Security | Never store private keys in cloud storage or version control |

### Key Management

| Practice | Description |
|----------|-------------|
| Separation | Use different keys for different services/accounts |
| Rotation | Regularly rotate your keys (every 6-12 months) |
| Compromise | If you suspect a key has been compromised, immediately revoke it from GitHub |

### Passphrase Protection

| Practice | Description |
|----------|-------------|
| Strength | Always use a strong passphrase |
| Storage | Consider using a password manager to store your passphrase |
| Sharing | Never share your passphrase with anyone |

### SSH Agent Security

| Command | Purpose |
|---------|---------|
| `ssh-agent` | Use to cache your key in memory |
| `ssh-add -D` | Clear the agent when you're done |
| `ssh-add -t 3600 ~/.ssh/id_ed25519` | Set a timeout for cached keys (3600 seconds = 1 hour) |

---

## 📝 Notes

- For new repositories, always use the SSH URL format: `git@github.com:username/repo.git`
- The SSH key passphrase is different from your GitHub password
- If you set up the SSH agent, you'll only need to enter your passphrase once per session
- Keep your private key (`id_ed25519`) secure and never share it
- You can use the same SSH key for multiple GitHub accounts by adding it to each account

---

## 🚨 Troubleshooting

### Common Error: "Permission denied (publickey)"

If you encounter this error:
```
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
```

**Solution steps:**
1. Verify your SSH key is properly added to GitHub (repeat Steps 3-4)
2. Test your SSH connection (Step 5)
3. Ensure you're using the SSH URL format for your repository (Step 6)
4. Check that your SSH agent is running and has your key loaded (see SSH Agent setup above)
5. Verify your SSH key file permissions are correct (see Security Best Practices below)

---

<div align="center">
  <p><strong>Happy secure coding!</strong></p>
</div> 