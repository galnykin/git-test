### 🔐 **What are SSH keys in Git?**

SSH keys are a secure way to authenticate with Git services (like GitHub, GitLab, Bitbucket) **without entering your username and password every time**.

They allow **Git to connect to remote repositories over SSH**, enabling you to:

* `git clone`
* `git push`
* `git pull`

with **secure, passwordless access**.

---

### 🧱 **SSH Key Pair = Two Parts**

1. **Private key** → Stays on your computer (`~/.ssh/id_ed25519`)
2. **Public key** → You copy this to GitHub/GitLab settings (`~/.ssh/id_ed25519.pub`)

The server recognises your private key because it matches the public one.

---

### 🛠️ **How to Set Up SSH with Git (Step-by-Step)**

#### 1. ✅ Generate a new SSH key:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Press Enter to accept the default path (`~/.ssh/id_ed25519`) and optionally add a passphrase.

#### 2. ✅ Start the ssh-agent:

```bash
eval "$(ssh-agent -s)"
```

#### 3. ✅ Add your private key to the agent:

```bash
ssh-add ~/.ssh/id_ed25519
```

#### 4. ✅ Add your public key to Git hosting service:

* Show the public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

* Copy the entire output
* Paste it into GitHub/GitLab:

  * **GitHub**: Settings → SSH and GPG Keys → New SSH Key
  * **GitLab**: Preferences → SSH Keys → Add Key

#### 5. ✅ Test your connection:

```bash
ssh -T git@github.com
```

If everything is OK, you'll see a message like:

> "Hi username! You've successfully authenticated..."

---

### ⚙️ Bonus: Use SSH URLs in your Git remotes

When cloning a repository, use the **SSH URL**, e.g.:

```bash
git@github.com:your-username/your-repo.git
```

instead of the HTTPS one like:

```bash
https://github.com/your-username/your-repo.git
```

---

