# yamlfmt-action

![GitHub release (latest by date)](https://img.shields.io/github/v/release/yk-lab/yamlfmt-action)
![GitHub license](https://img.shields.io/github/license/yk-lab/yamlfmt-action)
![GitHub stars](https://img.shields.io/github/stars/yk-lab/yamlfmt-action?style=social)

[English](README.md) | 日本語

YAML ファイルを自動的に整形するための GitHub Actions 用アクションです。コードの一貫性を保ち、レビューやデバッグを容易にします。

## TL;DR

```yaml
name: YAML Formatting

on:
  push:
    branches:
      - main
  pull_request:
    types: [opened, synchronize, reopened]
  workflow_dispatch:

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: yamllint
        uses: reviewdog/action-yamllint@v1
        with:
          github_token: ${{ secrets.github_token }}
          fail_on_error: true
      - name: yamlfmt
        uses: yk-lab/yamlfmt-action@v1
```

## 特徴

- **自動フォーマット**: `yamlfmt` を使用して YAML ファイルを統一的に整形。
- **簡単導入**: 既存のワークフローに数行追加するだけで利用可能。
- **柔軟な設定**: `yamlfmt` のオプションをカスタマイズ可能。
- **高速**: 軽量で高速な動作。

## 目次

- [使用方法](#使用方法)
- [オプション](#オプション)
- [よくある質問](#よくある質問)
- [貢献](#貢献)
- [ライセンス](#ライセンス)
- [関連リンク](#関連リンク)

## 使用方法

ワークフローのステップに `yk-lab/yamlfmt-action` を追加します。

```yaml
name: YAML Formatting

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  format:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run yamlfmt
        uses: yk-lab/yamlfmt-action@v1
```

## オプション

アクションには以下の入力パラメータがあります。

- `version`: `yamlfmt` のバージョン (デフォルト: `latest`, 例: `v0.13.0`)
- `path`: フォーマットする YAML ファイルまたはディレクトリのパス
- `dstar`: ダブルスター展開を有効にする
- `exclude`: 指定したパターンに一致するファイルを除外
- `gitignore_excludes`: `.gitignore` で指定したパターンに一致するファイルを除外
- `gitignore_path`: `.gitignore` ファイルのパス
- `extensions`: フォーマットするファイルの拡張子のリスト
- `formatter`: 使用するフォーマッタを設定

### パラメータの使用例

```yaml
- name: Run yamlfmt
  uses: yk-lab/yamlfmt-action@v1
  with:
    path: '.github/workflows'
```

## よくある質問

### Q1. `yamlfmt` の設定ファイルを使用できますか？

A1. はい、`.yamlfmt.yaml` などの設定ファイルをリポジトリに含めることで、`yamlfmt` の挙動をカスタマイズできます。

### Q2. 特定のファイルやディレクトリを除外できますか？

A2. 現在のバージョンでは、`yamlfmt` のオプションを使用して除外パターンを指定できます。詳しくは [yamlfmt のドキュメント](https://github.com/google/yamlfmt)をご覧ください。

## 貢献

貢献を歓迎します！バグ報告や機能提案は [Issues](https://github.com/yk-lab/yamlfmt-action/issues) へ、コードの貢献はプルリクエストをお送りください。

**開発手順：**

1. リポジトリをフォークします。
2. 新しいブランチを作成します。`git checkout -b feature/your-feature`
3. 変更をコミットします。`git commit -m 'Add some feature'`
4. ブランチをプッシュします。`git push origin feature/your-feature`
5. プルリクエストを作成します。

## ライセンス

このプロジェクトは [MIT ライセンス](LICENSE)のもとで公開されています。

## 関連リンク

- [yamlfmt リポジトリ](https://github.com/google/yamlfmt)
- [GitHub Actions ドキュメント](https://docs.github.com/ja/actions)
- [他の GitHub Actions](https://github.com/marketplace?type=actions)
