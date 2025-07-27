# 技術ステアリング: 仕様駆動開発CLI

## 1. アーキテクチャ概要

このプロジェクトは、Pythonで構築されたコマンドラインインターフェース（CLI）ツールです。モジュール式で拡張可能に設計されており、将来的に新しいコマンドや機能を追加できます。

## 2. 技術スタック

- **言語**: Python 3.x
- **CLIフレームワーク**: `click`（または`argparse`のような類似のライブラリ）
- **ファイルI/O**: ファイルおよびディレクトリ操作のための標準Pythonライブラリ
- **テスト**: 単体テストおよび統合テストのための`pytest`

## 3. 開発環境

- **バージョン管理**: Git
- **パッケージ管理**: `pip`および`requirements.txt`
- **コードフォーマット**: `black`
- **リンティング**: `ruff`

## 4. 主要コマンド

- `gemini steering`: ステアリングドキュメントを管理します。
- `gemini spec init [feature-name]`: 新しい仕様を初期化します。
- `gemini spec requirements [feature-name]`: 仕様の要件を生成します。
- `gemini spec design [feature-name]`: 仕様の技術設計を生成します。
- `gemini spec tasks [feature-name]`: 仕様の実装タスクを生成します。
- `gemini spec status [feature-name]`: 仕様のステータスを確認します。

## 5. データ管理

- **仕様**: `.kiro/specs`ディレクトリ内にマークダウンファイルとして保存されます。
- **設定**: プロジェクトレベルの設定は、`.kiro/steering`内のステアリングドキュメントを通じて管理されます。