# {SECTION_NAME} ドキュメント

```yaml
@metadata
type: "navigation_readme"
intent: "{SECTION_NAME}関連ドキュメントのナビゲーション"
context:
  project: "${project_name}"
  section: "{section_name}"
  parent: "{parent_path}"
  children: {children_list}
capabilities: {capabilities_list}
scope: {scope_list}
```

{PROJECT_NAME}プロジェクトの{SECTION_NAME}に関するドキュメント群です。

## 📋 ドキュメント一覧

### 🔧 {MAIN_CATEGORY}
{MAIN_DOCS_LIST}

### 📚 {SUB_CATEGORY_1}
{SUB_DOCS_LIST_1}

### 🛠️ {SUB_CATEGORY_2}
{SUB_DOCS_LIST_2}

### 🔗 {SUB_CATEGORY_3}
{SUB_DOCS_LIST_3}

## 🎯 {SECTION_NAME}概要

### アーキテクチャ

```mermaid
graph TB
{ARCHITECTURE_DIAGRAM}
```

### 技術スタック

| 領域 | 技術 | 用途 |
|------|------|------|
{TECH_STACK_TABLE}

## 🚀 クイックスタート

### 前提条件

```yaml
@prerequisites
requirements:
{REQUIREMENTS_LIST}
```

### セットアップ手順

```bash
# 環境構築
{SETUP_COMMANDS}
```

### 開発・実行

```bash
# 開発サーバー起動
{DEV_COMMANDS}

# テスト実行
{TEST_COMMANDS}

# ビルド
{BUILD_COMMANDS}
```

## 📊 メトリクス・パフォーマンス

### パフォーマンス指標

| 指標 | 目標値 | 現在値 | 測定方法 |
|------|--------|--------|----------|
{METRICS_TABLE}

### 制約・制限

```yaml
@constraints
{CONSTRAINTS_DEFINITION}
```

## 🔧 開発・運用ガイド

### 開発環境

```bash
# ローカル開発環境構築
{LOCAL_DEV_SETUP}
```

### 本番環境

```bash
# 本番デプロイ
{PRODUCTION_DEPLOY}
```

### トラブルシューティング

{TROUBLESHOOTING_SECTION}

## 🔗 関連リンク

- **[メインプロジェクト]({MAIN_PROJECT_LINK})** - {PROJECT_NAME}全体概要
{RELATED_LINKS}

---

> **📝 このドキュメントについて**  
> このファイルは **[DocsTemplate](../../../DocsTemplate/project/navigation-readme-template.md)** から生成されました。  
> 更新時は対応するテンプレートも合わせて更新してください。
