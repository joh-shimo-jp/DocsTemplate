# {PROJECT_NAME}（バックエンド）ドキュメント

```yaml
@metadata
type: "backend_readme"
intent: "バックエンド関連ドキュメントのナビゲーション"
context:
  project: "${project_name}"
  layer: "backend"
  parent: "../../README.md"
  children:
    - "./setup-guide.md"
    - "./development-guide.md"
    - "./api-reference.md"
capabilities:
  - "API提供"
  - "データ処理"
  - "ビジネスロジック"
  - "外部連携"
scope:
  - "サーバーサイド処理"
  - "データベース操作"
  - "API設計・実装"
```

{PROJECT_NAME}は、{LANGUAGE}ベースの{API_TYPE}システムです。{DESCRIPTION}

## 📋 ドキュメント一覧

### 🔧 開発関連
- **[セットアップガイド](./setup-guide.md)** - {LANGUAGE}環境構築と設定
- **[開発ガイド](./development-guide.md)** - 開発手順とベストプラクティス
- **[テストガイド](./testing-guide.md)** - テスト戦略と実行方法

### 🏗️ アーキテクチャ
- **[システム設計書](./system-architecture.md)** - バックエンド全体設計
- **[データベース設計](./database-design.md)** - DB設計と操作
- **[処理エンジン設計](./engine-architecture.md)** - コア処理エンジン

### 🤖 AI・外部連携
- **[AI連携設計](./ai-integration.md)** - 外部AI統合仕様
- **[外部API連携](./external-api.md)** - 外部サービス統合
- **[認証・認可](./authentication.md)** - セキュリティ設計

### 🔌 API・インターフェース
- **[APIリファレンス](./api-reference.md)** - エンドポイント仕様
- **[エッジデプロイ](./edge-deploy.md)** - エッジ環境デプロイ設計
- **[フロントエンド連携](./frontend-integration.md)** - フロントエンド連携仕様

## 🧱 ディレクトリ構成

```plaintext
{BACKEND_DIR}/
├── {MAIN_MODULE}/         # メインモジュール
│   ├── {ENTRY_POINT}     # アプリケーションエントリーポイント
│   ├── models/           # データモデル
│   ├── services/         # ビジネスロジック
│   └── utils/            # ユーティリティ
├── api/                  # APIエンドポイント
│   ├── routes/           # ルート定義
│   ├── middleware/       # ミドルウェア
│   └── schemas/          # APIスキーマ
├── tests/                # テストコード
├── {CONFIG_FILE}         # 依存関係
└── README.md             # セットアップガイド
```

## 🚀 クイックスタート

```yaml
@quickstart
environment_setup:
  - "仮想環境作成"
  - "依存関係インストール"
  - "設定ファイル準備"
server_startup:
  - "開発サーバー起動"
  - "テスト実行"
```

```bash
# 仮想環境作成・有効化
{VENV_CREATE_COMMAND}
{VENV_ACTIVATE_COMMAND}

# 依存関係のインストール
{INSTALL_COMMAND}

# サーバー起動
{SERVER_START_COMMAND}

# テスト実行
{TEST_COMMAND}
```

## 🔗 関連リンク

- **[メインプロジェクト](../../README.md)** - {PROJECT_NAME}全体概要
- **[フロントエンド](../{FRONTEND_DOC_DIR}/README.md)** - フロントエンドドキュメント
- **[インフラストラクチャ](../infrastructure/README.md)** - インフラ設計書

---

> **📝 このドキュメントについて**  
> このファイルは **[DocsTemplate](../../../DocsTemplate/project/backend-readme-template.md)** から生成されました。  
> 更新時は対応するテンプレートも合わせて更新してください。
