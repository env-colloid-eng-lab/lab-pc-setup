# Git と GitHub

研究室で最低限必要な Git / GitHub の使い方だけをこのページにまとめます。
より詳しい説明・運用ルールは以下を参照してください：

- [https://github.com/kaityo256/github](https://github.com/kaityo256/github)

## 1. Git のインストール

Windows では、作業スタイルに合わせてどちらかを選びます：

- **Windows + WSL**：WSL で Python / Linux 系ツールを使う場合はこちら。
- **Windows ネイティブ**：PowerShell や Windows アプリ中心で使う場合はこちら。
- **macOS**：`brew install git`（[macOS セットアップ](mac.md) を参照）
- **Linux**：`sudo apt install -y git`

### Windows + WSL

WSL を使う場合は、Git は Windows ではなく **Ubuntu 側**に入れます。

Ubuntu ターミナルで以下を実行します：

```bash
sudo apt update
sudo apt install -y git
git --version
```

その後、Git の初期設定を行います：

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

### Windows ネイティブ

WSL を使わない場合は、[Git for Windows](https://gitforwindows.org/) をインストールします。

PowerShell で `winget` が使える場合は以下を実行します：

```powershell
winget install --id Git.Git -e --source winget
```

または、[Git for Windows 公式サイト](https://gitforwindows.org/) や [Git downloads](https://git-scm.com/downloads) からインストーラーをダウンロードします。

インストール後、PowerShell を開き直して確認します：

```powershell
git --version
```

Git の初期設定を行います：

```powershell
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

## 2. Git の初期設定（1 回だけ）

上の Windows 手順で初期設定まで済ませた場合は、この手順は不要です。

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```

## 3. GitHub アカウントの作成

まだアカウントを持っていない場合は、GitHub で無料アカウントを作成します：
[https://github.com/](https://github.com/)

大学・研究室・個人のメールアドレスを使ってください。

## 4. GitHub の認証設定

初心者はまず **HTTPS** を使うのがおすすめです。

- **Windows ネイティブ**：Git for Windows に含まれる Git Credential Manager を使います。HTTPS で clone / push すると、ブラウザ認証が開きます。
- **Windows + WSL**：HTTPS も使えます。必要に応じて GitHub CLI または SSH を使います。
- **macOS / Linux**：HTTPS が使えます。GitHub CLI や SSH もよく使われます。

参考：[GitHub Docs](https://docs.github.com/)

### 方法 A：HTTPS

GitHub に表示される HTTPS URL を使います。
初回の `clone` / `pull` / `push` 時に、ブラウザでのサインインや、GitHub のユーザー名と Personal Access Token（PAT）の入力を求められることがあります。
Windows ネイティブでは Git Credential Manager により、認証情報が保存されることが多いです。

クローン用の具体的なコマンドは、後半の「クローン」手順にまとめています。

### 方法 B：GitHub CLI

```bash
# macOS
brew install gh

# Ubuntu / WSL
sudo apt install gh

# 認証（対話形式で進めます）
gh auth login
```

`gh auth login` の途中で「What is your preferred protocol for Git operations?」と聞かれたら、SSH を設定済みでない限り **HTTPS** を選択してください。

### 方法 C：SSH キー

授業・研究室・プロジェクトで SSH を指定された場合に使います。

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
cat ~/.ssh/id_ed25519.pub
```

表示された公開鍵を GitHub の **Settings → SSH and GPG keys → New SSH key** に登録します。

## 5. 研究室でよく使う最小ワークフロー

### 5-1. リポジトリをローカルにクローン

初心者は HTTPS から始めるのがおすすめです：

```bash
git clone https://github.com/<ユーザー名>/<リポジトリ名>.git
cd <リポジトリ名>
```

GitHub CLI を使う場合：

```bash
gh repo clone <ユーザー名>/<リポジトリ名>
cd <リポジトリ名>
```

SSH を使う場合：

```bash
git clone git@github.com:<ユーザー名>/<リポジトリ名>.git
cd <リポジトリ名>
```

### 5-2. 変更を保存して GitHub に反映

```bash
git status
git add .
git commit -m "変更内容"
git push
```

### 5-3. 作業前に最新状態を取得

```bash
git pull
```

## 6. まず困ったら確認するコマンド

```bash
git status
git log --oneline -n 5
git remote -v
```

---

詳細（ブランチ運用、コンフリクト解消、Pull Request の流れなど）は以下を必ず参照してください：

- [https://github.com/kaityo256/github](https://github.com/kaityo256/github)

---

[← セットアップ概要へ戻る](index.md)
