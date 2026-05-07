# Windows / WSL のセットアップ

このガイドでは、Windows に Windows Subsystem for Linux（WSL）をセットアップする手順を説明します。WSL は開発作業に推奨される Linux 環境を提供します。

## 1. WSL の有効化

**PowerShell** を管理者として開き、以下を実行します：

```powershell
wsl --install
```

WSL 2 と Ubuntu がデフォルトでインストールされます。プロンプトに従ってコンピューターを再起動してください。

## 2. Ubuntu の初期設定

再起動後、Ubuntu が起動し、Linux ユーザー名とパスワードの設定を求められます。  
シンプルなユーザー名（英小文字、スペースなし）と覚えやすいパスワードを設定してください。

## 3. パッケージの更新

Ubuntu のターミナルで以下を実行します：

```bash
sudo apt update && sudo apt upgrade -y
```

## 4. 基本ツールのインストール

```bash
sudo apt install -y git curl wget build-essential
```

## 5. VS Code との連携

VS Code に **WSL** 拡張機能をインストールします。その後、以下のコマンドで任意のフォルダーを WSL 環境で開けます：

```bash
code .
```

VS Code が起動し、WSL 環境に自動的に接続されます。

## 6. 次のステップ

- WSL 内に [Miniforge](miniforge.md) をインストールする
- [Git と GitHub](git-github.md) を設定する

---

*注意：WSL 2 には Windows 10 バージョン 2004 以降、または Windows 11 が必要です。*

---

[← セットアップ概要へ戻る](index.md)
