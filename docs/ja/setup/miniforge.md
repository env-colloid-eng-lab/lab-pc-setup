# Miniforge

本研究室では、Python 環境の管理に Miniforge を推奨します。

- Miniforge は conda-forge が提供する軽量な conda/mamba ディストリビューションである。
- 既定で conda-forge チャンネルを使用する。
- `conda` と `mamba` の両方を利用できる。
- 本研究室では、再現性の高い Python 環境を作るために Miniforge を推奨する。

このページでは、新しく Miniforge をインストールする手順を標準として説明します。既に Anaconda、Miniconda、Mambaforge、古い Miniforge などをインストールしている場合は、特別な理由がなければ先に削除してから Miniforge を入れ直してください。

## 0. 既に Anaconda、Miniconda、その他の conda をインストールしている場合

このラボのセットアップガイドでは、多くの場合、新しい Miniforge を入れ直す方法を推奨します。既に Anaconda、Miniconda、Mambaforge、古い Miniforge などの conda 系ディストリビューションをインストールしている場合は、Miniforge をインストールする前に削除してください。

### Windows

1. VS Code、ターミナル、Jupyter など、Python を使用している可能性のあるアプリを閉じます。
2. **設定** → **アプリ** → **インストールされているアプリ**を開きます。
3. **Anaconda**、**Miniconda**、**Mambaforge**、**Miniforge** など、古い conda 系ディストリビューションをアンインストールします。
4. インストール先フォルダーが残っている場合は削除します。よくある場所は次の通りです。
   - `C:\Users\<ユーザー名>\anaconda3`
   - `C:\Users\<ユーザー名>\miniconda3`
   - `C:\Users\<ユーザー名>\mambaforge`
   - `C:\Users\<ユーザー名>\miniforge3`
5. Windows の検索欄から **ユーザー環境変数の編集**を開き、`Path` に残っている古い conda 関連の項目を削除します。例：`anaconda3`、`miniconda3`、`mambaforge`、`miniforge3` を含むパス。
6. 新しいターミナルを開き、古いコマンドが残っていないか確認します。

```powershell
conda --version
```

コマンドが見つからない状態になっていれば、新しい Miniforge のインストールに進んでください。

### macOS / Ubuntu / Linux / WSL

古い `conda` コマンドが使えるターミナルを開き、以下を実行します。

```bash
conda init --reverse --dry-run
conda init --reverse

CONDA_BASE_ENVIRONMENT="$(conda info --base)"
echo "次のコマンドで削除される場所: ${CONDA_BASE_ENVIRONMENT}"
rm -rf "${CONDA_BASE_ENVIRONMENT}"

rm -f "${HOME}/.condarc"
rm -rf "${HOME}/.conda"
```

コマンドが終わったら、ターミナルを閉じてください。その後、新しいターミナルを開いて Miniforge をインストールします。

## 1. Windows

1. Miniforge のリリースページを開きます。  
   [https://github.com/conda-forge/miniforge/releases/latest](https://github.com/conda-forge/miniforge/releases/latest)
2. Windows 用インストーラー **`Miniforge3-Windows-x86_64.exe`** をダウンロードします。
3. インストーラーを実行します。
4. 特別な理由がなければ **Just Me** を選びます。
5. インストール先は既定の場所、通常は `C:\Users\<ユーザー名>\miniforge3` のままで構いません。
6. スタートメニューにショートカットを作成する既定の設定はそのままにします。
7. 理由が分からない場合は、Miniforge をシステムの `Path` に追加しないでください。
8. インストール後、スタートメニューから **Miniforge Prompt** を開きます。
9. 以下を実行します。

```powershell
conda --version
mamba --version
```

Windows 上で通常の作業をする場合は、conda や mamba のコマンドを **Miniforge Prompt** で実行します。WSL2 内で作業する場合は、Windows 側ではなく Ubuntu 側に Miniforge をインストールしてください。詳しくは [WSL2 に関する注意](#4-wsl2-に関する注意) を参照してください。

## 2. macOS

1. **ターミナル**を開きます。
2. 使用している Mac に合ったインストーラーをダウンロードします。

```bash
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
```

3. インストーラーを実行します。

```bash
bash Miniforge3-$(uname)-$(uname -m).sh
```

4. 画面の指示に従います。conda を初期化するか聞かれたら `yes` と答えてください。
5. ターミナルを閉じ、新しいターミナルを開きます。
6. インストールを確認します。

```bash
conda --version
mamba --version
```

Miniforge 公式プロジェクトでは macOS 用の `.pkg` インストーラーも提供されています。このハンドブックでは、Intel Mac と Apple Silicon Mac のどちらでも同じ流れで使えるため、上記のシェルインストーラーを推奨します。

## 3. Ubuntu / Linux

1. ターミナルを開きます。
2. 必要に応じて、ダウンロード用の基本ツールをインストールします。

```bash
sudo apt update
sudo apt install -y curl wget
```

3. 使用している Linux に合った Miniforge インストーラーをダウンロードします。

```bash
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
```

4. インストーラーを実行します。

```bash
bash Miniforge3-$(uname)-$(uname -m).sh
```

5. 画面の指示に従います。conda を初期化するか聞かれたら `yes` と答えてください。
6. ターミナルを閉じ、新しいターミナルを開きます。
7. インストールを確認します。

```bash
conda --version
mamba --version
```

## 4. WSL2 に関する注意

Windows で WSL2 を使う場合、WSL2 内の Ubuntu は Windows とは別の Linux 環境として考えます。

- Miniforge は **Ubuntu ターミナル**の中にインストールします。PowerShell ではありません。
- WSL2 内では、上の Ubuntu / Linux の手順を使ってください。
- WSL2 の Python 環境には、Windows 用の Miniforge インストーラーを使わないでください。
- ラボのプロジェクトファイルは、可能であれば `/mnt/c/...` ではなく、`~/projects` など Linux 側のファイルシステムに置いてください。
- VS Code では **WSL** 拡張機能を使い、WSL2 内の Miniforge 環境の Python インタープリターを選択します。

## 5. ラボ用 Python パッケージを準備する

ラボ用の作業には、専用の環境を作成します。以下の例では、`lab-python` という名前の環境に、よく使う科学技術計算用 Python パッケージをインストールします。

```bash
mamba create -n lab-python python=3.11 numpy pandas matplotlib seaborn scipy scikit-learn jupyterlab ipykernel openpyxl
conda activate lab-python
```

何らかの理由で `mamba` が使えない場合は、同じパッケージ一覧で `conda` を使ってください。

```bash
conda create -n lab-python python=3.11 numpy pandas matplotlib seaborn scipy scikit-learn jupyterlab ipykernel openpyxl
conda activate lab-python
```

次回以降、新しいターミナルで作業を始めるときは、先に環境を有効化します。

```bash
conda activate lab-python
```

## 6. インストールを確認する

`lab-python` を有効化したあと、以下を実行します。

```bash
conda info
conda env list
python --version
python -c "import numpy, pandas, matplotlib; print('Python environment is ready')"
```

以下を確認できれば成功です。

- Miniforge のインストール先が表示される。多くの場合、パスの末尾は `miniforge3` です。
- 既定のチャンネルとして `conda-forge` が表示される。
- 環境一覧に `lab-python` が表示される。
- Python のバージョン番号が表示される。
- `Python environment is ready` と表示される。

## 7. 参考リンク

- [Miniforge GitHub repository](https://github.com/conda-forge/miniforge)
- [Latest Miniforge releases](https://github.com/conda-forge/miniforge/releases/latest)
- [conda-forge](https://conda-forge.org/)

---

[← セットアップ概要へ戻る](index.md)
