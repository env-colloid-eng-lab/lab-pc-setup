# macOS Setup

This guide covers the initial setup steps for macOS before installing Python and other development tools.

## 1. Install Xcode Command Line Tools

Open **Terminal** (Applications → Utilities → Terminal) and run:

```bash
xcode-select --install
```

Follow the on-screen prompts to install the tools. This provides Git, Make, and other essential build tools.

## 2. Install Homebrew (Recommended)

Homebrew is a popular package manager for macOS:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow the instructions in the terminal. After installation, run:

```bash
brew update
```

## 3. Install Git (via Homebrew)

```bash
brew install git
```

Verify:

```bash
git --version
```

## 4. Next Steps

- Install [Miniforge](miniforge.md) for Python environment management
- Install [VS Code & Python](vscode-python.md)
- Set up [Git & GitHub](git-github.md)

---

*Note: These instructions apply to both Intel and Apple Silicon (M1/M2/M3) Macs. Homebrew handles architecture differences automatically.*

---

[← Back to Setup Overview](index.md)
