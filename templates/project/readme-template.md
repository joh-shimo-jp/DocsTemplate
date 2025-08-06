# {Project Name} プロジェクトREADMEテンプレート

```yaml
@metadata
type: "project_readme_template"
version: "1.0.0"
intent: "{Project Name}のプロジェクト概要・目的・構成説明テンプレート"
context:
  project: "{project_name}"
  layer: "project_root"
  parent: null
  children:
    - "./docs/*"
    - "./src/*"
    - "./architecture-template.md"
    - "./tech-stack-template.md"
capabilities:
  - "プロジェクト概要説明"
  - "セットアップ手順提供"
  - "ドキュメント構成ナビゲーション"
  - "開発ガイドライン"
  - "貢献者向け情報"
scope:
  - "プロジェクト全体概要"
  - "技術仕様概要"
  - "開発環境情報"
  - "運用・保守情報"
```

## 📑 目次

1. [思想とコンセプト](#-思想とコンセプト)
   - [基本理念](#-基本理念)
   - [デザイン原則](#-デザイン原則)
2. [プロジェクト構成](#-プロジェクト構成と技術スタック)
   - [リポジトリ構成](#-リポジトリ構成)
   - [技術スタック](#-技術スタック)
3. [セットアップと利用](#-セットアップと利用)
4. [開発計画](#-開発計画)
5. [ライセンス](#-ライセンス)

## 📜 思想とコンセプト

### 🎯 基本理念

```yaml
@concept
core_idea: "プロジェクトのコアアイデア"
principles:
  - description: "基本理念1"
    details: "説明"
  - description: "基本理念2"
    details: "説明"
```

### 🧠 デザイン原則

- **原則1**: 説明
- **原則2**: 説明
- **原則3**: 説明

## 🧱 プロジェクト構成と技術スタック

### 📦 リポジトリ構成
```
project_name/
├── src/              # ソースコード
├── docs/             # ドキュメント
├── tests/            # テストコード
└── README.md         # このファイル
```

### � 技術スタック
- フレームワーク
- ライブラリ
- ツール

## ⚙️ セットアップと利用

```yaml
@setup
prerequisites:
  - "必要条件1"
  - "必要条件2"
steps:
  - phase: "インストール"
    commands:
      - "command1"
      - "command2"
  - phase: "設定"
    commands:
      - "command3"
      - "command4"
```

### 関連ドキュメント

- **[フロントエンドドキュメント](./docs/frontend/README.md)** - UI・フロントエンド関連ドキュメント
- **[バックエンドドキュメント](./docs/backend/README.md)** - API・バックエンド関連ドキュメント
- **[インフラストラクチャ設計書](./docs/infrastructure/README.md)** - インフラ全体ナビゲーション
- **[AI制約定義](./shared/config/ai-constraints.yaml)** - AI動作制約とガイドライン

> **📝 ドキュメント作成について**  
> 新しいドキュメントの作成時は、**[DocsTemplate](../DocsTemplate/)を利用**してください。  
> AI駆動開発に最適化されたテンプレート群により、一貫性のある高品質なドキュメントを効率的に作成できます。

## 📊 開発状況

```yaml
@development_status
current_phase: "phase_name"
progress:
  completed:
    - name: "完了した機能1"
      date: "YYYY-MM-DD"
      version: "1.0.0"
    - name: "完了した機能2"
      date: "YYYY-MM-DD"
      version: "1.1.0"
  in_progress:
    - name: "開発中の機能1"
      status: "実装中"
      completion: 75
    - name: "開発中の機能2"
      status: "テスト中"
      completion: 90
  planned:
    - name: "計画中の機能1"
      priority: "high"
      target_version: "1.2.0"
    - name: "計画中の機能2"
      priority: "medium"
      target_version: "1.3.0"
```

### 🎯 マイルストーン進捗

| 🧩 フェーズ | 内容 | 状態 | 完了予定 |
|------------|------|------|----------|
| **Phase 1** | コア機能の実装 | ✅ 完了 | YYYY-MM |
| **Phase 2** | 拡張機能の追加 | � 進行中 (80%) | YYYY-MM |
| **Phase 3** | 最適化とテスト | � 計画中 | YYYY-MM |

### 📈 最近の更新
- YYYY-MM-DD: 機能Aの実装完了
- YYYY-MM-DD: 機能Bのベータ版リリース
- YYYY-MM-DD: バグ修正とパフォーマンス改善

## 📜 ライセンス

このプロジェクトは[ライセンス名](./LICENSE)の下で公開されています。
