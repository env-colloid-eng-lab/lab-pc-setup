# macOS のセットアップ

このガイドでは、Python やその他の開発ツールをインストールする前に必要な macOS の初期設定手順を説明します。

## 1. Xcode コマンドラインツールのインストール

**ターミナル**（アプリケーション → ユーティリティ → ターミナル）を開き、以下を実行します：

```bash
xcode-select --install
```

画面の指示に従ってインストールを完了します。Git、Make などの基本的なビルドツールが提供されます。

## 2. Homebrew のインストール（推奨）

Homebrew は macOS 向けの人気パッケージマネージャーです：

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

ターミナルの指示に従ってインストールします。インストール後、以下を実行します：

```bash
brew update
```

## 3. Git のインストール（Homebrew 経由）

```bash
brew install git
```

確認：

```bash
git --version
```

## 4. 次のステップ

- [Miniforge](miniforge.md) で Python 環境を管理する
- [VS Code と Python](vscode-python.md) をインストールする
- [Git と GitHub](git-github.md) を設定する

---

*注意：これらの手順は Intel Mac および Apple Silicon（M1/M2/M3）Mac の両方に対応しています。Homebrew がアーキテクチャの違いを自動的に処理します。*

---

[← セットアップ概要へ戻る](index.md)
