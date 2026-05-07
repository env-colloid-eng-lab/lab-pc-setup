# Miniforge

Miniforge is the recommended Python environment manager for this lab.

- Miniforge is a minimal conda/mamba distribution maintained by conda-forge.
- It uses the conda-forge channel by default.
- It provides both `conda` and `mamba` commands.
- This lab recommends Miniforge for reproducible Python environments.

This page assumes a fresh Miniforge installation. If you already have Anaconda, Miniconda, Mambaforge, or an older Miniforge installation, remove it first unless you have a specific reason to keep it.

## 0. If you already have Anaconda, Miniconda, or another conda installed

For most users following this lab setup guide, a fresh Miniforge installation is recommended. If you already installed a conda-based distribution such as Anaconda, Miniconda, Mambaforge, or an older Miniforge, uninstall it before installing Miniforge.

### Windows

1. Close VS Code, terminals, Jupyter, and any program that may be using Python.
2. Open **Settings** → **Apps** → **Installed apps**.
3. Uninstall any old conda distribution, for example **Anaconda**, **Miniconda**, **Mambaforge**, or **Miniforge**.
4. If the installation folder remains, delete it. Common folders include:
   - `C:\Users\<your-user-name>\anaconda3`
   - `C:\Users\<your-user-name>\miniconda3`
   - `C:\Users\<your-user-name>\mambaforge`
   - `C:\Users\<your-user-name>\miniforge3`
5. In the Windows search box, open **Edit environment variables for your account** and remove old conda-related entries from `Path`, such as `anaconda3`, `miniconda3`, `mambaforge`, or `miniforge3` paths.
6. Open a new terminal and check that the old command is gone:

```powershell
conda --version
```

If the command is no longer found, continue with the fresh Miniforge installation below.

### macOS / Ubuntu / Linux / WSL

Open a terminal where the old `conda` command is available, then run:

```bash
conda init --reverse --dry-run
conda init --reverse

CONDA_BASE_ENVIRONMENT="$(conda info --base)"
echo "The next command will remove: ${CONDA_BASE_ENVIRONMENT}"
rm -rf "${CONDA_BASE_ENVIRONMENT}"

rm -f "${HOME}/.condarc"
rm -rf "${HOME}/.conda"
```

Close the terminal after these commands finish. Then open a new terminal before installing Miniforge.

## 1. Windows

1. Open the Miniforge releases page:
   [https://github.com/conda-forge/miniforge/releases/latest](https://github.com/conda-forge/miniforge/releases/latest)
2. Download the Windows installer named **`Miniforge3-Windows-x86_64.exe`**.
3. Run the installer.
4. Use **Just Me** unless you have a reason to install for all users.
5. Install to the default location, usually `C:\Users\<your-user-name>\miniforge3`.
6. Keep the default option that creates Start Menu shortcuts.
7. Do **not** add Miniforge to the system `Path` unless you understand why you need it.
8. After installation, open **Miniforge Prompt** from the Start Menu.
9. Run:

```powershell
conda --version
mamba --version
```

For normal lab work on Windows, use **Miniforge Prompt** when running conda or mamba commands. If you are working inside WSL2, install Miniforge inside Ubuntu instead; see [WSL2 notes](#4-wsl2-notes).

## 2. macOS

1. Open **Terminal**.
2. Download the correct installer for your Mac:

```bash
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
```

3. Run the installer:

```bash
bash Miniforge3-$(uname)-$(uname -m).sh
```

4. Follow the prompts. When asked whether to initialize conda, answer `yes`.
5. Close Terminal and open a new Terminal window.
6. Check the installation:

```bash
conda --version
mamba --version
```

The official Miniforge project also provides `.pkg` installers for macOS. The shell installer above is recommended in this handbook because it works consistently for both Intel and Apple Silicon Macs.

## 3. Ubuntu / Linux

1. Open a terminal.
2. Install basic download tools if needed:

```bash
sudo apt update
sudo apt install -y curl wget
```

3. Download the Miniforge installer for your Linux system:

```bash
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
```

4. Run the installer:

```bash
bash Miniforge3-$(uname)-$(uname -m).sh
```

5. Follow the prompts. When asked whether to initialize conda, answer `yes`.
6. Close the terminal and open a new terminal.
7. Check the installation:

```bash
conda --version
mamba --version
```

## 4. WSL2 notes

If you use Windows with WSL2, treat Ubuntu inside WSL2 as a separate Linux computer.

- Install Miniforge inside the **Ubuntu terminal**, not PowerShell.
- Use the Ubuntu / Linux instructions above inside WSL2.
- Do not use the Windows Miniforge installer for WSL2 Python environments.
- Keep lab project files inside the Linux filesystem, for example under `~/projects`, rather than under `/mnt/c/...` when possible.
- In VS Code, use the **WSL** extension and select the Python interpreter from the Miniforge environment inside WSL2.

## 5. Set up Python packages for lab use

Create a separate environment for lab work. The example below creates an environment named `lab-python` with common scientific Python packages.

```bash
mamba create -n lab-python python=3.11 numpy pandas matplotlib seaborn scipy scikit-learn jupyterlab ipykernel openpyxl
conda activate lab-python
```

If `mamba` is not available for any reason, use `conda` with the same package list:

```bash
conda create -n lab-python python=3.11 numpy pandas matplotlib seaborn scipy scikit-learn jupyterlab ipykernel openpyxl
conda activate lab-python
```

When you start a new terminal later, activate the environment before working:

```bash
conda activate lab-python
```

## 6. Check the installation

Run these commands after activating `lab-python`:

```bash
conda info
conda env list
python --version
python -c "import numpy, pandas, matplotlib; print('Python environment is ready')"
```

You should see:

- a Miniforge installation path, often ending in `miniforge3`;
- `conda-forge` listed as the default channel;
- the `lab-python` environment in the environment list;
- a Python version number;
- the message `Python environment is ready`.

## 7. References

- [Miniforge GitHub repository](https://github.com/conda-forge/miniforge)
- [Latest Miniforge releases](https://github.com/conda-forge/miniforge/releases/latest)
- [conda-forge](https://conda-forge.org/)

---

[← Back to Setup Overview](index.md)
