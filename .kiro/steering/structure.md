# 構造ステアリング: 仕様駆動開発CLI

## 1. ディレクトリ構造

```
.kiro/
├── steering/
│   ├── product.md
│   ├── tech.md
│   └── structure.md
└── specs/
    └── [feature-name]/
        ├── requirements.md
        ├── design.md
        ├── tasks.md
        └── spec.json
docs/
src/
    └── cli/
        ├── __init__.py
        ├── main.py
        ├── commands/
        │   ├── __init__.py
        │   ├── steering.py
        │   └── spec.py
        └── utils/
            ├── __init__.py
            └── file_io.py
tests/
    ├── __init__.py
    ├── test_spec.py
    └── test_steering.py
.gitignore
GEMINI.md
README.md
requirements.txt
```

## 2. コードパターンと規約

- **CLIコマンド**: 各コマンドグループ（例：`spec`、`steering`）は、`src/cli/commands`ディレクトリ内の独自のモジュールに配置する必要があります。
- **モジュール性**: 関数は小さく、単一のタスクに集中させます。共通の操作には`src/cli/utils`のユーティリティ関数を使用します。
- **エラーハンドリング**: `try...except`ブロックを使用して潜在的なエラーを適切に処理し、ユーザーに明確なエラーメッセージを提供します。
- **テスト**: すべての新しい機能に対して単体テストを作成します。必要なテストデータと環境を設定するために`pytest`のフィクスチャを使用します。

## 3. 命名規則

- **モジュール**: `snake_case.py`
- **クラス**: `PascalCase`
- **関数と変数**: `snake_case`
- **定数**: `UPPER_SNAKE_CASE`
- **CLIコマンド**: `kebab-case`（例：`spec-init`）