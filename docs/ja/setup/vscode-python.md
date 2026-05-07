# VS Code と Python

このガイドでは、Visual Studio Code をインストールし、Python 開発のために設定する手順を説明します。

## 1. Visual Studio Code のインストール

公式サイトから VS Code をダウンロードしてインストールします：  
[https://code.visualstudio.com/](https://code.visualstudio.com/)

お使いの OS（Windows、macOS、Linux）向けのインストーラーに従ってください。

## 2. Python 拡張機能のインストール

1. VS Code を開きます。
2. **拡張機能**パネルを開きます（Ctrl+Shift+X / Cmd+Shift+X）。
3. **Python**（Microsoft 製）を検索します。
4. **インストール**をクリックします。

## 3. Python インタープリターの選択

1. コマンドパレットを開きます（Ctrl+Shift+P / Cmd+Shift+P）。
2. `Python: Select Interpreter` と入力します。
3. Miniforge 環境の Python インタープリターを選択します（設定済みの場合）。

> Miniforge をまだセットアップしていない場合は、先に [Miniforge のセットアップ](miniforge.md) を行ってください。

## 4. セットアップの確認

まず、VS Code の右下のステータスバーに表示される Python インタープリター名を確認してください。ここに、選択した Miniforge 環境の Python が表示されていれば、VS Code 上ではそのインタープリターが使われます。

> `Python: Select Interpreter` でインタープリターを選択しても、統合ターミナル上の `python` コマンドが自動でその環境を指すとは限りません。

ターミナルでも確認したい場合は、VS Code 内でターミナルを開き（ターミナル → 新しいターミナル）、対象の conda 環境を有効化してから確認します：

```bash
conda activate <環境名>
python --version
```

`Python 3.11.x` のようなバージョン番号が表示されれば成功です。`<環境名>` には、選択した Miniforge 環境名を指定してください。

## 5. 便利な拡張機能（任意）

- **Pylance** — Python の IntelliSense を強化
- **Jupyter** — VS Code 内で Jupyter Notebook を実行
- **GitLens** — Git の高度な統合機能

---

[← セットアップ概要へ戻る](index.md)
