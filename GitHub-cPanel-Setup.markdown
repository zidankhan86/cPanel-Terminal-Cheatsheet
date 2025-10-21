# Quick Setup: GitHub with cPanel

## Step 1: Generate SSH Key on Your Server
1. Log in to your cPanel server via SSH.
2. Run the following command to generate an SSH key:
   ```
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```
3. Press `Enter` for all prompts to accept defaults (avoid setting a passphrase to prevent issues with cPanel deploy scripts).
4. This creates two files:
   - `~/.ssh/id_ed25519` (private key)
   - `~/.ssh/id_ed25519.pub` (public key)

## Step 2: Copy the Public Key
1. Display the public key by running:
   ```
   cat ~/.ssh/id_ed25519.pub
   ```
2. Copy the full output (it starts with `ssh-ed25519 ...`).

## Step 3: Add Key to GitHub
1. Go to GitHub → **Settings** → **SSH and GPG Keys**.
2. Click **New SSH Key** or **Add SSH Key**.
3. Paste the copied public key into the provided field.
4. Click **Add SSH Key** to save.

## Step 4: Test SSH Connection
1. Verify the connection by running:
   ```
   ssh -T git@github.com
   ```
2. If successful, you’ll see a message like:
   ```
   Hi username! You've successfully authenticated, but GitHub does not provide shell access.
   ```

## Step 5: Clone the Private Repository in cPanel
1. Clone your private repository using:
   ```
   git clone git@github.com:username/private-repo.git
   ```