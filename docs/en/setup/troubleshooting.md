# Troubleshooting

This page lists common issues and their solutions. If your issue is not listed here, please open a GitHub Issue in this repository.

---

## conda: command not found

**Cause:** Miniconda was installed but the shell was not restarted, or conda was not initialized.

**Fix:**

```bash
source ~/.bashrc   # Linux / WSL
source ~/.zshrc    # macOS (zsh)
```

If that does not work, re-run the Miniconda installer and answer `yes` to the initialization prompt.

---

## Python version is wrong

**Cause:** The system Python is being used instead of the conda environment Python.

**Fix:** Make sure you have activated your environment:

```bash
conda activate myenv
python --version
```

---

## VS Code does not find Python

**Fix:**
1. Open the Command Palette (Ctrl+Shift+P / Cmd+Shift+P).
2. Type `Python: Select Interpreter`.
3. Choose the correct Python path (usually under `~/miniconda3/envs/...`).

---

## Git push asks for password repeatedly

**Cause:** You are using HTTPS instead of SSH, or credentials are not cached.

**Fix:** Switch to SSH authentication. See [Git & GitHub](git-github.md) for setup instructions.

---

## WSL cannot connect to the internet

**Fix:** On WSL, `/etc/resolv.conf` is often auto-generated at startup, so editing it directly may only be temporary.

To make the DNS change persist, disable auto-generation first:

```ini
[network]
generateResolvConf = false
```

Save that in `/etc/wsl.conf`, then restart WSL from PowerShell:

```powershell
wsl --shutdown
```

Reopen the Ubuntu terminal and recreate `/etc/resolv.conf` with your preferred DNS server:

```bash
sudo rm -f /etc/resolv.conf
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf
```

---

## Homebrew installation fails on macOS

**Fix:** Make sure Xcode Command Line Tools are installed first:

```bash
xcode-select --install
```

Then retry the Homebrew installation.

---

[← Back to Setup Overview](index.md)
