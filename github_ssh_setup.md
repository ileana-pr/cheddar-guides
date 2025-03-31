# Setting up SSH Keys with GitHub from Command Line

## Prerequisites
- Git installed
- WSL (Windows Subsystem for Linux) or Linux terminal
- GitHub account

## Step 1: Check for Existing SSH Keys
```bash
ls -la ~/.ssh
```
If you see files like `id_ed25519` or `id_rsa`, you already have SSH keys. You have two options:

### Option A: Use Existing Key
If you want to use your existing key, you can skip to Step 3 to copy and add it to GitHub.

### Option B: Create New Key
If you want to create a new key instead:
1. Back up your existing key (optional but recommended):
```bash
mv ~/.ssh/id_ed25519 ~/.ssh/id_ed25519.backup
mv ~/.ssh/id_ed25519.pub ~/.ssh/id_ed25519.pub.backup
```
2. Continue with Step 2 to generate a new key

## About SSH Key Types
We use `ed25519` because it's currently the most secure and efficient SSH key type available. It's:
- Faster than RSA keys
- More secure (resistant to quantum computer attacks)
- Shorter key length while maintaining high security
- Recommended by GitHub and other major platforms

The older RSA key type (which you might see as `id_rsa`) is still widely used but is gradually being phased out in favor of ed25519.

## Step 2: Generate New SSH Key
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
- Press Enter to accept the default file location (`/home/your_username/.ssh/id_ed25519`)
- Choose whether to set a passphrase:
  - Setting a passphrase is recommended for security
  - You can press Enter twice for no passphrase (less secure but more convenient)

## Step 3: Copy Your Public Key
```bash
cat ~/.ssh/id_ed25519.pub
```
Copy the entire output (starts with `ssh-ed25519` and ends with your email)

## Step 4: Add SSH Key to GitHub
1. Go to GitHub.com → Settings
2. Click "SSH and GPG keys" in the left sidebar
3. Click "New SSH key"
4. Give it a title (e.g., "WSL Ubuntu")
5. Paste your public key
6. Click "Add SSH key"

## Step 5: Test SSH Connection
```bash
ssh -T git@github.com
```
You should see: "Hi username! You've successfully authenticated, but GitHub does not provide shell access."

## Step 6: Update Repository Remote URL
If you have an existing repository using HTTPS, update it to use SSH:
```bash
git remote set-url origin git@github.com:username/repository.git
```

## Optional: Set Up SSH Agent (Recommended)
To avoid entering your passphrase repeatedly, you can set up the SSH agent:

1. Start the SSH agent:
```bash
eval "$(ssh-agent -s)"
```

2. Add your SSH key to the agent:
```bash
ssh-add ~/.ssh/id_ed25519
```

3. Enter your passphrase once when prompted

## SSH Key Security Best Practices
1. **File Permissions**
   - Set correct permissions on your SSH directory and keys:
   ```bash
   chmod 700 ~/.ssh
   chmod 600 ~/.ssh/id_ed25519
   chmod 644 ~/.ssh/id_ed25519.pub
   ```
   - This ensures only you can read/write your private key

2. **Backup Your Keys**
   - Keep a secure backup of your private key (`id_ed25519`)
   - Store backups in an encrypted location (password manager, encrypted drive)
   - Never store private keys in cloud storage or version control

3. **Key Management**
   - Use different keys for different services/accounts
   - Regularly rotate your keys (every 6-12 months)
   - If you suspect a key has been compromised, immediately revoke it from GitHub

4. **Passphrase Protection**
   - Always use a strong passphrase
   - Consider using a password manager to store your passphrase
   - Never share your passphrase with anyone

5. **SSH Agent Security**
   - Use `ssh-agent` to cache your key in memory
   - Clear the agent when you're done: `ssh-add -D`
   - Set a timeout for cached keys: `ssh-add -t 3600 ~/.ssh/id_ed25519`

## Notes
- For new repositories, always use the SSH URL format: `git@github.com:username/repo.git`
- The SSH key passphrase is different from your GitHub password
- If you set up the SSH agent, you'll only need to enter your passphrase once per session
- Keep your private key (`id_ed25519`) secure and never share it
- You can use the same SSH key for multiple GitHub accounts by adding it to each account 