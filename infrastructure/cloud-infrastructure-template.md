# クラウドインフラ設計書テンプレート

```yaml
@metadata
type: "infrastructure-design"
version: "1.0.0"
intent: "クラウドインフラストラクチャの設計と構築ガイド"
capabilities:
  - "クラウドリソース定義"
  - "スケーラビリティ設計"
  - "コスト最適化"
  - "セキュリティ設計"
scope:
  - "アーキテクチャ設計"
  - "リソース設計"
  - "ネットワーク設計"
  - "ストレージ設計"
context:
  project: "{PROJECT_NAME}"
  cloud_provider: "{CLOUD_PROVIDER}" # AWS/GCP/Azure
  environment: "{ENVIRONMENT}" # dev/staging/prod
```

## 📑 ナビゲーション

1. [設計概要](#-設計概要)
2. [アーキテクチャ設計](#-アーキテクチャ設計)
3. [リソース設計](#-リソース設計)
4. [ネットワーク設計](#-ネットワーク設計)
5. [ストレージ設計](#-ストレージ設計)
6. [セキュリティ設計](#-セキュリティ設計)
7. [スケーラビリティ設計](#-スケーラビリティ設計)
8. [コスト設計](#-コスト設計)
9. [構築手順](#-構築手順)
10. [運用考慮事項](#-運用考慮事項)

## 🎯 設計概要

### 基本情報
- **プロジェクト名**: {PROJECT_NAME}
- **クラウドプロバイダー**: {CLOUD_PROVIDER}
- **環境**: {ENVIRONMENT}
- **設計者**: {DESIGNER_NAME}
- **設計日**: {DESIGN_DATE}
- **更新日**: {UPDATE_DATE}

### 設計目標
```yaml
@design_goals
performance:
  - "{PERFORMANCE_REQUIREMENT_1}"
  - "{PERFORMANCE_REQUIREMENT_2}"
availability:
  - "可用性: {AVAILABILITY_TARGET}%"
  - "復旧時間: {RTO_TARGET}"
  - "復旧ポイント: {RPO_TARGET}"
scalability:
  - "最大同時接続数: {MAX_CONNECTIONS}"
  - "スケーリング戦略: {SCALING_STRATEGY}"
security:
  - "{SECURITY_REQUIREMENT_1}"
  - "{SECURITY_REQUIREMENT_2}"
```

### 制約条件
- **予算制約**: {BUDGET_CONSTRAINT}
- **技術制約**: {TECHNICAL_CONSTRAINT}
- **コンプライアンス**: {COMPLIANCE_REQUIREMENT}
- **期限**: {DEADLINE}

## 🏗️ アーキテクチャ設計

### 全体アーキテクチャ
```yaml
@architecture
layers:
  presentation:
    components:
      - name: "{FRONTEND_SERVICE}"
        type: "{SERVICE_TYPE}"
        instances: {INSTANCE_COUNT}
  application:
    components:
      - name: "{BACKEND_SERVICE}"
        type: "{SERVICE_TYPE}"
        instances: {INSTANCE_COUNT}
  data:
    components:
      - name: "{DATABASE_SERVICE}"
        type: "{DATABASE_TYPE}"
        instances: {INSTANCE_COUNT}
```

### システム構成図
```
[ここにアーキテクチャ図を配置]

例：
Internet → Load Balancer → Frontend Services → Backend Services → Database
                ↓
            Static Assets (CDN)
```

### データフロー
1. **リクエストフロー**: {REQUEST_FLOW_DESCRIPTION}
2. **データ処理フロー**: {DATA_PROCESSING_FLOW}
3. **レスポンスフロー**: {RESPONSE_FLOW_DESCRIPTION}

## 🔧 リソース設計

### {CLOUD_PROVIDER}リソース一覧

#### コンピューティングリソース
| リソース名 | タイプ | スペック | 数量 | 用途 |
|------------|--------|----------|------|------|
| {COMPUTE_RESOURCE_1} | {INSTANCE_TYPE} | {SPEC} | {COUNT} | {PURPOSE} |
| {COMPUTE_RESOURCE_2} | {INSTANCE_TYPE} | {SPEC} | {COUNT} | {PURPOSE} |

#### ネットワークリソース
| リソース名 | タイプ | 設定 | 用途 |
|------------|--------|------|------|
| {NETWORK_RESOURCE_1} | {NETWORK_TYPE} | {CONFIG} | {PURPOSE} |
| {NETWORK_RESOURCE_2} | {NETWORK_TYPE} | {CONFIG} | {PURPOSE} |

#### ストレージリソース
| リソース名 | タイプ | 容量 | IOPS | 用途 |
|------------|--------|------|------|------|
| {STORAGE_RESOURCE_1} | {STORAGE_TYPE} | {CAPACITY} | {IOPS} | {PURPOSE} |
| {STORAGE_RESOURCE_2} | {STORAGE_TYPE} | {CAPACITY} | {IOPS} | {PURPOSE} |

### リソース配置戦略
```yaml
@placement_strategy
availability_zones:
  - zone_1: "{AZ_1}"
    resources: ["{RESOURCE_LIST}"]
  - zone_2: "{AZ_2}"
    resources: ["{RESOURCE_LIST}"]
regions:
  primary: "{PRIMARY_REGION}"
  backup: "{BACKUP_REGION}"
```

## 🌐 ネットワーク設計

### ネットワーク構成
```yaml
@network_design
vpc:
  cidr: "{VPC_CIDR}"
  name: "{VPC_NAME}"
subnets:
  public:
    - name: "{PUBLIC_SUBNET_1}"
      cidr: "{SUBNET_CIDR}"
      az: "{AZ}"
  private:
    - name: "{PRIVATE_SUBNET_1}"
      cidr: "{SUBNET_CIDR}"
      az: "{AZ}"
```

### セキュリティグループ/ファイアウォール
| 名前 | 方向 | プロトコル | ポート | ソース/デスティネーション |
|------|------|------------|--------|---------------------------|
| {SG_NAME_1} | {DIRECTION} | {PROTOCOL} | {PORT} | {SOURCE_DEST} |
| {SG_NAME_2} | {DIRECTION} | {PROTOCOL} | {PORT} | {SOURCE_DEST} |

### ロードバランサー設定
- **タイプ**: {LB_TYPE}
- **アルゴリズム**: {LB_ALGORITHM}
- **ヘルスチェック**: {HEALTH_CHECK_CONFIG}
- **SSL終端**: {SSL_TERMINATION}

## 💾 ストレージ設計

### データベース設計
```yaml
@database_design
primary_database:
  type: "{DB_TYPE}"
  engine: "{DB_ENGINE}"
  version: "{DB_VERSION}"
  instance_class: "{INSTANCE_CLASS}"
  storage:
    type: "{STORAGE_TYPE}"
    size: "{STORAGE_SIZE}GB"
    iops: {IOPS_COUNT}
backup:
  strategy: "{BACKUP_STRATEGY}"
  retention: "{RETENTION_PERIOD}"
  schedule: "{BACKUP_SCHEDULE}"
```

### ファイルストレージ
| 用途 | ストレージタイプ | 容量 | アクセス頻度 | 暗号化 |
|------|------------------|------|--------------|--------|
| {PURPOSE_1} | {STORAGE_TYPE} | {CAPACITY} | {ACCESS_FREQUENCY} | {ENCRYPTION} |
| {PURPOSE_2} | {STORAGE_TYPE} | {CAPACITY} | {ACCESS_FREQUENCY} | {ENCRYPTION} |

### CDN設定
- **プロバイダー**: {CDN_PROVIDER}
- **オリジン**: {ORIGIN_CONFIG}
- **キャッシュ戦略**: {CACHE_STRATEGY}
- **地理的分散**: {GEO_DISTRIBUTION}

## 🔒 セキュリティ設計

### アクセス制御
```yaml
@access_control
iam_policies:
  - name: "{POLICY_NAME}"
    permissions: ["{PERMISSION_LIST}"]
    resources: ["{RESOURCE_LIST}"]
service_accounts:
  - name: "{SA_NAME}"
    purpose: "{PURPOSE}"
    permissions: ["{PERMISSION_LIST}"]
```

### 暗号化設定
| 対象 | 暗号化方式 | キー管理 | 備考 |
|------|------------|----------|------|
| {ENCRYPTION_TARGET_1} | {ENCRYPTION_METHOD} | {KEY_MANAGEMENT} | {NOTES} |
| {ENCRYPTION_TARGET_2} | {ENCRYPTION_METHOD} | {KEY_MANAGEMENT} | {NOTES} |

### ネットワークセキュリティ
- **WAF設定**: {WAF_CONFIG}
- **DDoS対策**: {DDOS_PROTECTION}
- **VPN設定**: {VPN_CONFIG}
- **侵入検知**: {IDS_CONFIG}

## 📈 スケーラビリティ設計

### オートスケーリング設定
```yaml
@autoscaling
horizontal_scaling:
  min_instances: {MIN_INSTANCES}
  max_instances: {MAX_INSTANCES}
  target_cpu: {TARGET_CPU}%
  scale_out_cooldown: {SCALE_OUT_TIME}
  scale_in_cooldown: {SCALE_IN_TIME}
vertical_scaling:
  enabled: {VERTICAL_SCALING_ENABLED}
  max_cpu: {MAX_CPU}
  max_memory: "{MAX_MEMORY}GB"
```

### 負荷分散戦略
- **分散アルゴリズム**: {DISTRIBUTION_ALGORITHM}
- **セッション管理**: {SESSION_MANAGEMENT}
- **故障時対応**: {FAILOVER_STRATEGY}

## 💰 コスト設計

### 月額コスト見積もり
| カテゴリ | リソース | 単価 | 数量 | 月額 |
|----------|----------|------|------|------|
| コンピューティング | {COMPUTE_RESOURCE} | ${UNIT_PRICE} | {QUANTITY} | ${MONTHLY_COST} |
| ストレージ | {STORAGE_RESOURCE} | ${UNIT_PRICE} | {QUANTITY} | ${MONTHLY_COST} |
| ネットワーク | {NETWORK_RESOURCE} | ${UNIT_PRICE} | {QUANTITY} | ${MONTHLY_COST} |
| **合計** | | | | **${TOTAL_MONTHLY_COST}** |

### コスト最適化施策
- **リザーブドインスタンス**: {RESERVED_INSTANCE_STRATEGY}
- **スポットインスタンス**: {SPOT_INSTANCE_USAGE}
- **ライフサイクル管理**: {LIFECYCLE_MANAGEMENT}
- **モニタリング**: {COST_MONITORING}

## 🛠️ 構築手順

### 前提条件
- [ ] {CLOUD_PROVIDER}アカウント設定完了
- [ ] CLI/SDKインストール完了
- [ ] 権限設定完了
- [ ] ドメイン準備完了

### 構築ステップ
1. **初期設定**
   ```bash
   # {CLOUD_PROVIDER}初期設定コマンド例
   {INITIAL_SETUP_COMMANDS}
   ```

2. **ネットワーク構築**
   ```bash
   # ネットワーク構築コマンド例
   {NETWORK_SETUP_COMMANDS}
   ```

3. **コンピューティングリソース構築**
   ```bash
   # コンピューティングリソース作成コマンド例
   {COMPUTE_SETUP_COMMANDS}
   ```

4. **ストレージ構築**
   ```bash
   # ストレージ構築コマンド例
   {STORAGE_SETUP_COMMANDS}
   ```

5. **セキュリティ設定**
   ```bash
   # セキュリティ設定コマンド例
   {SECURITY_SETUP_COMMANDS}
   ```

### 構築後確認項目
- [ ] 全リソースが正常に作成されている
- [ ] ネットワーク接続が正常
- [ ] セキュリティ設定が適用されている
- [ ] 監視設定が動作している
- [ ] バックアップが設定されている

## 🔧 運用考慮事項

### 監視項目
```yaml
@monitoring
metrics:
  - name: "{METRIC_NAME}"
    threshold: {THRESHOLD_VALUE}
    action: "{ACTION}"
logs:
  - service: "{SERVICE_NAME}"
    log_level: "{LOG_LEVEL}"
    retention: "{RETENTION_PERIOD}"
alerts:
  - name: "{ALERT_NAME}"
    condition: "{ALERT_CONDITION}"
    notification: "{NOTIFICATION_METHOD}"
```

### バックアップ戦略
- **データベース**: {DB_BACKUP_STRATEGY}
- **ファイルシステム**: {FILE_BACKUP_STRATEGY}
- **設定ファイル**: {CONFIG_BACKUP_STRATEGY}
- **復旧テスト**: {RECOVERY_TEST_SCHEDULE}

### メンテナンス計画
| 項目 | 頻度 | 内容 | 担当者 |
|------|------|------|--------|
| {MAINTENANCE_ITEM_1} | {FREQUENCY} | {DESCRIPTION} | {OWNER} |
| {MAINTENANCE_ITEM_2} | {FREQUENCY} | {DESCRIPTION} | {OWNER} |

### トラブルシューティング
#### よくある問題と対処法
1. **{COMMON_ISSUE_1}**
   - 症状: {SYMPTOM}
   - 原因: {CAUSE}
   - 対処法: {SOLUTION}

2. **{COMMON_ISSUE_2}**
   - 症状: {SYMPTOM}
   - 原因: {CAUSE}
   - 対処法: {SOLUTION}

#### 緊急時連絡先
- **運用チーム**: {OPERATIONS_CONTACT}
- **開発チーム**: {DEVELOPMENT_CONTACT}
- **{CLOUD_PROVIDER}サポート**: {CLOUD_SUPPORT_CONTACT}

---

## 📝 変更履歴

| 日付 | バージョン | 変更者 | 変更内容 |
|------|------------|--------|----------|
| {DATE} | {VERSION} | {AUTHOR} | {CHANGE_DESCRIPTION} |

## 📚 参考資料

- [{CLOUD_PROVIDER}公式ドキュメント]({OFFICIAL_DOCS_URL})
- [ベストプラクティス]({BEST_PRACTICES_URL})
- [設計パターン]({DESIGN_PATTERNS_URL})
- [コスト最適化ガイド]({COST_OPTIMIZATION_URL})
