# CI/CDパイプライン設計書テンプレート

```yaml
@metadata
type: "cicd-pipeline-design"
version: "1.0.0"
intent: "継続的インテグレーション・デプロイメントパイプラインの設計と構築"
capabilities:
  - "自動ビルド設計"
  - "自動テスト設計"
  - "自動デプロイ設計"
  - "品質ゲート設計"
scope:
  - "ソースコード管理"
  - "ビルドプロセス"
  - "テストプロセス"
  - "デプロイプロセス"
context:
  project: "{PROJECT_NAME}"
  repository: "{REPOSITORY_URL}"
  environments: ["{ENV_LIST}"]
```

## 📑 ナビゲーション

1. [パイプライン概要](#-パイプライン概要)
2. [ブランチ戦略](#-ブランチ戦略)
3. [ビルドプロセス](#-ビルドプロセス)
4. [テストプロセス](#-テストプロセス)
5. [デプロイプロセス](#-デプロイプロセス)
6. [品質ゲート](#-品質ゲート)
7. [環境管理](#-環境管理)
8. [セキュリティ](#-セキュリティ)
9. [監視・通知](#-監視通知)
10. [トラブルシューティング](#-トラブルシューティング)

## 🎯 パイプライン概要

### 基本情報
- **プロジェクト名**: {PROJECT_NAME}
- **リポジトリ**: {REPOSITORY_URL}
- **CI/CDツール**: {CICD_TOOL}
- **設計者**: {DESIGNER_NAME}
- **設計日**: {DESIGN_DATE}

### パイプライン目標
```yaml
@pipeline_goals
automation:
  - "ビルド自動化率: {BUILD_AUTOMATION_RATE}%"
  - "テスト自動化率: {TEST_AUTOMATION_RATE}%"
  - "デプロイ自動化率: {DEPLOY_AUTOMATION_RATE}%"
quality:
  - "コードカバレッジ: {CODE_COVERAGE_TARGET}%以上"
  - "品質ゲート通過率: {QUALITY_GATE_RATE}%以上"
  - "セキュリティ脆弱性: {SECURITY_THRESHOLD}以下"
performance:
  - "ビルド時間: {BUILD_TIME_TARGET}分以内"
  - "テスト実行時間: {TEST_TIME_TARGET}分以内"
  - "デプロイ時間: {DEPLOY_TIME_TARGET}分以内"
```

### パイプラインフロー
```
開発者 → Git Push → CI Trigger → Build → Test → Quality Gate → Deploy
                      ↓
                   Artifacts → Container Registry → Staging → Production
```

## 🌿 ブランチ戦略

### Git Flow戦略
```yaml
@git_flow
main_branches:
  - name: "main"
    purpose: "本番環境用"
    protection: true
    auto_deploy: true
    target_env: "production"
  - name: "develop"
    purpose: "開発環境用"
    protection: true
    auto_deploy: true
    target_env: "development"
feature_branches:
  - pattern: "feature/*"
    purpose: "機能開発用"
    merge_target: "develop"
    ci_trigger: true
release_branches:
  - pattern: "release/*"
    purpose: "リリース準備用"
    merge_target: ["main", "develop"]
    ci_trigger: true
hotfix_branches:
  - pattern: "hotfix/*"
    purpose: "緊急修正用"
    merge_target: ["main", "develop"]
    ci_trigger: true
```

### プルリクエスト戦略
- **レビュー要件**: {REVIEW_REQUIREMENTS}
- **承認者数**: {APPROVER_COUNT}名以上
- **CI通過**: 必須
- **コンフリクト解決**: マージ前に必須

## 🔧 ビルドプロセス

### ビルド環境
```yaml
@build_environment
runtime:
  - name: "{RUNTIME_NAME}"
    version: "{RUNTIME_VERSION}"
dependencies:
  - "{DEPENDENCY_1}"
  - "{DEPENDENCY_2}"
tools:
  - name: "{BUILD_TOOL}"
    version: "{TOOL_VERSION}"
cache:
  enabled: true
  locations: ["{CACHE_LOCATION_1}", "{CACHE_LOCATION_2}"]
```

### ビルドステップ
#### フロントエンド（例：{FRONTEND_FRAMEWORK}）
```yaml
build_steps:
  1_dependency_install:
    command: "{DEPENDENCY_INSTALL_COMMAND}"
    cache_key: "package-lock"
  2_lint_check:
    command: "{LINT_COMMAND}"
    fail_on_error: true
  3_build:
    command: "{BUILD_COMMAND}"
    artifacts: ["{BUILD_ARTIFACTS}"]
  4_test:
    command: "{TEST_COMMAND}"
    coverage: true
```

#### バックエンド（例：{BACKEND_FRAMEWORK}）
```yaml
build_steps:
  1_dependency_install:
    command: "{DEPENDENCY_INSTALL_COMMAND}"
    cache_key: "requirements"
  2_security_scan:
    command: "{SECURITY_SCAN_COMMAND}"
    fail_on_high: true
  3_lint_check:
    command: "{LINT_COMMAND}"
    fail_on_error: true
  4_unit_test:
    command: "{UNIT_TEST_COMMAND}"
    coverage: true
  5_build:
    command: "{BUILD_COMMAND}"
    artifacts: ["{BUILD_ARTIFACTS}"]
```

### アーティファクト管理
| アーティファクト | 形式 | 保存場所 | 保存期間 |
|------------------|------|----------|----------|
| {ARTIFACT_1} | {FORMAT} | {STORAGE_LOCATION} | {RETENTION_PERIOD} |
| {ARTIFACT_2} | {FORMAT} | {STORAGE_LOCATION} | {RETENTION_PERIOD} |

## 🧪 テストプロセス

### テスト戦略
```yaml
@test_strategy
unit_tests:
  framework: "{UNIT_TEST_FRAMEWORK}"
  coverage_threshold: {UNIT_COVERAGE_THRESHOLD}%
  parallel: true
integration_tests:
  framework: "{INTEGRATION_TEST_FRAMEWORK}"
  environment: "{TEST_ENVIRONMENT}"
  data: "{TEST_DATA_STRATEGY}"
e2e_tests:
  framework: "{E2E_TEST_FRAMEWORK}"
  browsers: ["{BROWSER_LIST}"]
  parallel: {E2E_PARALLEL_COUNT}
performance_tests:
  tool: "{PERFORMANCE_TEST_TOOL}"
  scenarios: ["{PERFORMANCE_SCENARIOS}"]
  thresholds:
    response_time: "{RESPONSE_TIME_THRESHOLD}ms"
    throughput: "{THROUGHPUT_THRESHOLD}req/s"
```

### テスト実行順序
1. **静的解析**: {STATIC_ANALYSIS_TOOLS}
2. **単体テスト**: 各コンポーネントの単体テスト
3. **統合テスト**: サービス間の統合テスト
4. **セキュリティテスト**: 脆弱性スキャン
5. **パフォーマンステスト**: 負荷テスト
6. **E2Eテスト**: エンドツーエンドシナリオテスト

### テスト環境
| 環境名 | 用途 | データ | 実行タイミング |
|--------|------|--------|----------------|
| {TEST_ENV_1} | {PURPOSE} | {TEST_DATA} | {TRIGGER_TIMING} |
| {TEST_ENV_2} | {PURPOSE} | {TEST_DATA} | {TRIGGER_TIMING} |

## 🚀 デプロイプロセス

### デプロイ戦略
```yaml
@deployment_strategy
environments:
  development:
    trigger: "push to develop"
    approval: false
    rollback: automatic
  staging:
    trigger: "merge to main"
    approval: false
    rollback: automatic
    smoke_tests: true
  production:
    trigger: "manual"
    approval: true
    approvers: ["{APPROVER_LIST}"]
    rollback: manual
    canary: true
    blue_green: true
```

### デプロイメント手順
#### ステージング環境
```yaml
staging_deployment:
  1_pre_deployment:
    - database_migration: "{MIGRATION_COMMAND}"
    - cache_clear: "{CACHE_CLEAR_COMMAND}"
  2_deployment:
    - container_deployment: "{DEPLOY_COMMAND}"
    - health_check: "{HEALTH_CHECK_COMMAND}"
  3_post_deployment:
    - smoke_tests: "{SMOKE_TEST_COMMAND}"
    - notification: "{NOTIFICATION_CONFIG}"
```

#### 本番環境
```yaml
production_deployment:
  1_pre_deployment:
    - approval_check: required
    - backup: "{BACKUP_COMMAND}"
    - maintenance_mode: enable
  2_deployment:
    - canary_deployment: 10%
    - monitoring: enable
    - validation: "{VALIDATION_COMMAND}"
    - full_deployment: conditional
  3_post_deployment:
    - health_check: "{HEALTH_CHECK_COMMAND}"
    - smoke_tests: "{SMOKE_TEST_COMMAND}"
    - maintenance_mode: disable
    - notification: "{NOTIFICATION_CONFIG}"
```

### ロールバック戦略
- **自動ロールバック条件**: {AUTO_ROLLBACK_CONDITIONS}
- **手動ロールバック手順**: {MANUAL_ROLLBACK_STEPS}
- **データベースロールバック**: {DB_ROLLBACK_STRATEGY}
- **ロールバック検証**: {ROLLBACK_VALIDATION}

## ✅ 品質ゲート

### 品質基準
```yaml
@quality_gates
code_quality:
  - metric: "code_coverage"
    threshold: {CODE_COVERAGE_THRESHOLD}%
    action: "block_deployment"
  - metric: "duplicated_lines"
    threshold: {DUPLICATED_LINES_THRESHOLD}%
    action: "warning"
security:
  - metric: "high_vulnerabilities"
    threshold: 0
    action: "block_deployment"
  - metric: "medium_vulnerabilities"
    threshold: {MEDIUM_VULN_THRESHOLD}
    action: "warning"
performance:
  - metric: "build_time"
    threshold: {BUILD_TIME_THRESHOLD}min
    action: "warning"
  - metric: "test_execution_time"
    threshold: {TEST_TIME_THRESHOLD}min
    action: "warning"
```

### 品質ツール
| ツール | 目的 | 実行タイミング | 結果の扱い |
|--------|------|----------------|------------|
| {QUALITY_TOOL_1} | {PURPOSE} | {TIMING} | {ACTION} |
| {QUALITY_TOOL_2} | {PURPOSE} | {TIMING} | {ACTION} |

## 🌍 環境管理

### 環境一覧
```yaml
@environments
development:
  purpose: "開発・実験用"
  infrastructure: "{DEV_INFRA}"
  database: "{DEV_DB}"
  external_apis: "mock"
  logging_level: "debug"
staging:
  purpose: "本番環境検証用"
  infrastructure: "{STAGING_INFRA}"
  database: "{STAGING_DB}"
  external_apis: "staging"
  logging_level: "info"
production:
  purpose: "本番サービス提供用"
  infrastructure: "{PROD_INFRA}"
  database: "{PROD_DB}"
  external_apis: "production"
  logging_level: "error"
```

### 環境設定管理
- **設定ファイル**: {CONFIG_FILE_STRATEGY}
- **環境変数**: {ENV_VAR_STRATEGY}
- **シークレット管理**: {SECRET_MANAGEMENT}
- **設定同期**: {CONFIG_SYNC_METHOD}

## 🔒 セキュリティ

### セキュリティチェック
```yaml
@security_checks
sast:
  tool: "{SAST_TOOL}"
  trigger: "every_commit"
  fail_on: "high_severity"
dast:
  tool: "{DAST_TOOL}"
  trigger: "staging_deployment"
  target: "{STAGING_URL}"
dependency_check:
  tool: "{DEPENDENCY_CHECK_TOOL}"
  trigger: "weekly"
  action: "create_issue"
container_scan:
  tool: "{CONTAINER_SCAN_TOOL}"
  trigger: "image_build"
  fail_on: "critical"
```

### アクセス制御
- **パイプライン実行権限**: {PIPELINE_PERMISSIONS}
- **本番デプロイ権限**: {PRODUCTION_DEPLOY_PERMISSIONS}
- **シークレットアクセス権限**: {SECRET_ACCESS_PERMISSIONS}
- **監査ログ**: {AUDIT_LOG_CONFIG}

## 📊 監視・通知

### 監視項目
```yaml
@monitoring
pipeline_metrics:
  - build_success_rate
  - build_duration
  - test_success_rate
  - deployment_frequency
  - lead_time
  - mttr
application_metrics:
  - response_time
  - error_rate
  - throughput
  - resource_usage
```

### 通知設定
| イベント | 通知先 | 通知方法 | 緊急度 |
|----------|--------|----------|--------|
| {EVENT_1} | {NOTIFICATION_TARGET} | {NOTIFICATION_METHOD} | {SEVERITY} |
| {EVENT_2} | {NOTIFICATION_TARGET} | {NOTIFICATION_METHOD} | {SEVERITY} |

### ダッシュボード
- **パイプライン概要**: {PIPELINE_DASHBOARD_URL}
- **品質メトリクス**: {QUALITY_DASHBOARD_URL}
- **デプロイメント状況**: {DEPLOYMENT_DASHBOARD_URL}

## 🔧 トラブルシューティング

### よくある問題と対処法

#### ビルド失敗
1. **依存関係エラー**
   - 症状: {DEPENDENCY_ERROR_SYMPTOM}
   - 対処法: {DEPENDENCY_ERROR_SOLUTION}

2. **テスト失敗**
   - 症状: {TEST_ERROR_SYMPTOM}
   - 対処法: {TEST_ERROR_SOLUTION}

#### デプロイ失敗
1. **環境不整合**
   - 症状: {ENV_ERROR_SYMPTOM}
   - 対処法: {ENV_ERROR_SOLUTION}

2. **リソース不足**
   - 症状: {RESOURCE_ERROR_SYMPTOM}
   - 対処法: {RESOURCE_ERROR_SOLUTION}

### 緊急時対応
- **緊急時連絡先**: {EMERGENCY_CONTACT}
- **エスカレーション手順**: {ESCALATION_PROCEDURE}
- **緊急デプロイ手順**: {EMERGENCY_DEPLOY_PROCEDURE}

### 有用なコマンド
```bash
# パイプライン状況確認
{PIPELINE_STATUS_COMMAND}

# ログ確認
{LOG_CHECK_COMMAND}

# 手動デプロイ
{MANUAL_DEPLOY_COMMAND}

# ロールバック
{ROLLBACK_COMMAND}
```

---

## 📝 変更履歴

| 日付 | バージョン | 変更者 | 変更内容 |
|------|------------|--------|----------|
| {DATE} | {VERSION} | {AUTHOR} | {CHANGE_DESCRIPTION} |

## 📚 参考資料

- [CI/CDベストプラクティス]({CICD_BEST_PRACTICES_URL})
- [{CICD_TOOL}公式ドキュメント]({CICD_TOOL_DOCS_URL})
- [デプロイメント戦略ガイド]({DEPLOYMENT_STRATEGY_URL})
- [品質ゲート設計ガイド]({QUALITY_GATE_URL})
