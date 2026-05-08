# Git & GitHub

This guide covers the basics of setting up Git and GitHub for version control.

## 1. Install Git

Choose the setup that matches how you will work on Windows:

- **Windows with WSL / Ubuntu**: choose this if you use Python or Linux-style tools in Ubuntu on WSL.
- **Windows native**: choose this if you mainly use PowerShell and Windows apps.
- **macOS**: `brew install git` (see [macOS setup](mac.md))
- **Linux**: `sudo apt install -y git`

### Windows with WSL / Ubuntu

If you use WSL, install Git inside **Ubuntu**, not on the Windows side.

Open an Ubuntu terminal and run:

```bash
sudo apt update
sudo apt install -y git
git --version
```

Then configure Git:

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

### Windows native

If you do not use WSL, install [Git for Windows](https://gitforwindows.org/).

If `winget` is available in PowerShell, run:

```powershell
winget install --id Git.Git -e --source winget
```

Or download the installer from the [Git for Windows website](https://gitforwindows.org/) or the [Git downloads page](https://git-scm.com/downloads).

After installation, close and reopen PowerShell, then check:

```powershell
git --version
```

Then configure Git:

```powershell
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

## 2. Configure Git

If you already configured Git in the Windows section above, skip this step.

Set your name and email (these will appear in your commit history):

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

## 3. Create a GitHub Account

If you do not have one, create a free account at:
[https://github.com/](https://github.com/)

Use your institutional or personal email address.

## 4. Authenticate with GitHub

For beginners, use **HTTPS** first.

- **Windows native**: Git for Windows includes Git Credential Manager. When you push or clone over HTTPS, sign in with the browser window that opens.
- **Windows with WSL / Ubuntu**: HTTPS also works, but on `git push` you may be prompted to authenticate. GitHub does **not** accept your account password for Git over HTTPS; use `gh auth login`, a credential helper, or a personal access token (PAT) if prompted.
- **macOS / Linux**: HTTPS works, but on `git push` you may be prompted to authenticate. GitHub does **not** accept your account password for Git over HTTPS; use `gh auth login`, a credential helper, or a personal access token (PAT) if prompted. SSH is also a common choice.

See also: [GitHub Docs](https://docs.github.com/)

### Option A: HTTPS

Use the HTTPS URL shown on GitHub:

```bash
git clone https://github.com/<username>/<repository>.git
```

### Option B: GitHub CLI

```bash
# Install gh (macOS)
brew install gh

# Install gh (Ubuntu/WSL)
sudo apt install gh

# Authenticate
gh auth login
```

When `gh auth login` asks for the protocol for Git operations, choose **HTTPS** unless you already use SSH.

### Option C: SSH Key

Use SSH if your course, lab, or project asks for it.

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
cat ~/.ssh/id_ed25519.pub
```

Copy the output and add it to GitHub: **Settings → SSH and GPG keys → New SSH key**.

## 5. Clone a Repository

For beginners, use HTTPS:

```bash
git clone https://github.com/<username>/<repository>.git
```

If you use GitHub CLI:

```bash
gh repo clone <username>/<repository>
```

If you use SSH:

```bash
git clone git@github.com:<username>/<repository>.git
```

## 6. Basic Git Workflow

```bash
git status           # check what has changed
git add .            # stage all changes
git commit -m "msg"  # commit with a message
git push             # push to GitHub
git pull             # pull latest changes
```

---

[← Back to Setup Overview](index.md)
