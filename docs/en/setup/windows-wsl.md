# Windows / WSL Setup

This guide explains how to set up the Windows Subsystem for Linux (WSL) on Windows, which provides a Linux environment recommended for development work.

## 1. Enable WSL

Open **PowerShell** as Administrator and run:

```powershell
wsl --install
```

This installs WSL 2 and Ubuntu by default. Restart your computer when prompted.

## 2. Set Up Ubuntu

After restarting, Ubuntu will launch and prompt you to create a Linux username and password.  
Choose a simple username (lowercase, no spaces) and a password you can remember.

## 3. Update Packages

Inside the Ubuntu terminal, run:

```bash
sudo apt update && sudo apt upgrade -y
```

## 4. Install Essential Tools

```bash
sudo apt install -y git curl wget build-essential
```

## 5. Integrate with VS Code

Install the **WSL** extension in VS Code. Then open any folder in WSL using:

```bash
code .
```

VS Code will launch and connect to the WSL environment automatically.

## 6. Next Steps

- Install [Miniforge](miniforge.md) inside WSL
- Set up [Git & GitHub](git-github.md)

---

*Note: WSL 2 requires Windows 10 version 2004 or later, or Windows 11.*

---

[← Back to Setup Overview](index.md)
