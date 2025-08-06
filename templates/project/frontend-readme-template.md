# {PROJECT_NAME}（フロントエンド）ドキュメント

```yaml
@metadata
type: "frontend_readme"
intent: "フロントエンド関連ドキュメントのナビゲーション"
context:
  project: "${project_name}"
  layer: "frontend"
  parent: "../../README.md"
  children:
    - "./development-guide.md"
    - "./architecture.md"
    - "./testing-guide.md"
capabilities:
  - "UI・UX設計"
  - "フロントエンド開発"
  - "状態管理"
  - "コンポーネント設計"
scope:
  - "ユーザーインターフェース"
  - "フロントエンド開発"
  - "クライアントサイド処理"
```

{PROJECT_NAME}は、{FRAMEWORK}ベースの{PROJECT_TYPE}アプリケーションです。{DESCRIPTION}

## 📋 ドキュメント一覧

### 🔧 開発関連
- **[開発ガイド](./development-guide.md)** - 開発手順とベストプラクティス
- **[セットアップガイド](../../{FRONTEND_DIR}/README.md)** - 環境構築と初期設定
- **[テストガイド](./testing-guide.md)** - テスト戦略と実行方法

### 🏗️ アーキテクチャ
- **[アーキテクチャ設計書](./architecture.md)** - システム設計と構造
- **[API連携ガイド](./api-integration.md)** - バックエンドとの連携設計
- **[状態管理設計](./state-management.md)** - 状態管理アーキテクチャ

### 🎨 UI/UX
- **[デザインシステム](./design-system.md)** - コンポーネント設計とテーマ
- **[ユーザビリティガイド](./usability-guide.md)** - UX設計原則
- **[アクセシビリティ](./accessibility.md)** - アクセシビリティ対応

### 🔌 連携・API
- **[バックエンド連携](./backend-integration.md)** - バックエンドとの通信設計
- **[外部API連携](./external-api.md)** - 外部サービス統合
- **[エッジコンピューティング連携](./edge-integration.md)** - エッジサービス連携

## 🧱 ディレクトリ構成

```plaintext
{FRONTEND_DIR}/
├── {SOURCE_DIR}/
│   ├── {ENTRY_POINT}      # アプリケーションエントリーポイント
│   ├── core/              # コア機能・設定
│   │   ├── config/        # 設定・定義
│   │   ├── model/         # データ構造体
│   │   └── services/      # API・バックエンド連携
│   ├── providers/         # 状態管理
│   ├── ui/                # ビュー・コンポーネント・テーマ
│   ├── utils/             # ユーティリティ
│   └── test/              # テストコード
├── {CONFIG_FILE}          # 依存関係設定
└── README.md              # セットアップガイド
```

## 🚀 クイックスタート

```yaml
@quickstart
steps:
  - phase: "依存関係インストール"
    commands:
      - "{INSTALL_COMMAND}"
  - phase: "アプリケーション実行"
    commands:
      - "{RUN_COMMAND}"
  - phase: "テスト実行"
    commands:
      - "{TEST_COMMAND}"
```

```bash
# 依存関係のインストール
{INSTALL_COMMAND}

# アプリケーションの実行
{RUN_COMMAND}

# テストの実行
{TEST_COMMAND}
```

## 🔗 関連リンク

- **[メインプロジェクト](../../README.md)** - {PROJECT_NAME}全体概要
- **[バックエンド](../{BACKEND_DOC_DIR}/README.md)** - バックエンドドキュメント
- **[インフラストラクチャ](../infrastructure/README.md)** - インフラ設計書

---

> **📝 このドキュメントについて**  
> このファイルは **[DocsTemplate](../../../DocsTemplate/project/frontend-readme-template.md)** から生成されました。  
> 更新時は対応するテンプレートも合わせて更新してください。
