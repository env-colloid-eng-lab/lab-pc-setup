# Git と GitHub

研究室で最低限必要な Git / GitHub の使い方だけをこのページにまとめます。  
より詳しい説明・運用ルールは以下を参照してください：

- [https://github.com/kaityo256/github](https://github.com/kaityo256/github)

## 1. Git のインストール

- **Windows（WSL / Ubuntu）**：`sudo apt install -y git`
- **macOS**：`brew install git`（[macOS セットアップ](mac.md) を参照）
- **Linux**：`sudo apt install -y git`

確認：

```bash
git --version
```

## 2. Git の初期設定（1 回だけ）

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

## 3. GitHub の認証設定（どちらか 1 つ）

### 方法 A：SSH キー

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
cat ~/.ssh/id_ed25519.pub
```

表示された公開鍵を GitHub の **Settings → SSH and GPG keys → New SSH key** に登録します。

### 方法 B：GitHub CLI

```bash
# macOS
brew install gh

# Ubuntu / WSL
sudo apt install gh

# 認証
gh auth login
```

## 4. 研究室でよく使う最小ワークフロー

### 4-1. リポジトリをローカルにクローン

```bash
git clone git@github.com:<ユーザー名>/<リポジトリ名>.git
cd <リポジトリ名>
```

### 4-2. 変更を保存して GitHub に反映

```bash
git status
git add .
git commit -m "変更内容"
git push
```

### 4-3. 作業前に最新状態を取得

```bash
git pull
```

## 5. まず困ったら確認するコマンド

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
