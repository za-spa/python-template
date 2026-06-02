# python-template

[copier](https://copier.readthedocs.io/) を使ったPythonプロジェクトのテンプレートです。

> [!NOTE]
> このテンプレートはVSCodeでの利用を前提とした設定（`.vscode/extensions.json`、`.vscode/settings.json`）が含まれています。

## 含まれるもの

| ツール | 用途 |
| --- | --- |
| [uv](https://docs.astral.sh/uv/) | パッケージ管理・仮想環境 |
| [ruff](https://docs.astral.sh/ruff/) | リンター・フォーマッター |
| [pyright](https://github.com/microsoft/pyright) | 型チェッカー |
| [pytest](https://pytest.org/) | テスト |
| [pre-commit](https://pre-commit.com/) | コミット前フック |
| [Task](https://taskfile.dev/) | タスクランナー |
| [GitHub Actions](https://github.com/features/actions) | CI（lint・型チェック・テストの自動実行） |

## 使い方

### 新規プロジェクトの作成

```bash
copier copy gh:za-spa/python-template <出力先ディレクトリ>
```

対話形式で以下を入力します：

| 項目 | 説明 |
| --- | --- |
| `project_name` | プロジェクト名 |
| `package_name` | Pythonパッケージ名（デフォルトはproject_nameから自動生成） |
| `python_version` | 使用するPythonバージョン（デフォルト: 3.12） |
| `is_package` | パッケージとしてインストールするか（デフォルト: true） |
| `has_cli` | CLIエントリーポイントを追加するか（デフォルト: false） |

### テンプレートの更新を既存プロジェクトに適用

```bash
copier update
```

## 生成されるプロジェクトの構成

```console
<project_name>/
├── .github/
│   └── workflows/
│       └── ci.yml
├── .vscode/
│   ├── extensions.json
│   └── settings.json
├── src/                      # is_package: true のときのみ生成
│   └── <package_name>/
│       └── __init__.py
├── tests/
│   ├── __init__.py
│   └── test_sample.py
├── .editorconfig
├── .gitignore
├── .pre-commit-config.yaml
├── .python-version
├── pyproject.toml
├── Taskfile.yaml
└── README.md
```

## 生成されたプロジェクトのコマンド

```bash
task setup      # 依存パッケージのインストールとpre-commitフックのセットアップ
task lint       # リンター実行
task format     # コードフォーマット
task test       # テスト実行
task typecheck  # 型チェック実行
```
