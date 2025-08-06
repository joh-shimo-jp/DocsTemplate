# 監視・運用設計書テンプレート

```yaml
@metadata
type: "monitoring-operations-design"
version: "1.0.0"
intent: "システム監視と運用管理の設計・実装ガイド"
capabilities:
  - "監視戦略設計"
  - "アラート管理"
  - "ログ管理"
  - "パフォーマンス監視"
  - "運用自動化"
scope:
  - "監視設計"
  - "ログ管理"
  - "アラート設計"
  - "ダッシュボード設計"
  - "運用プロセス"
context:
  project: "{PROJECT_NAME}"
  environments: ["{ENVIRONMENT_LIST}"]
  monitoring_tools: ["{MONITORING_TOOL_LIST}"]
```

## 📑 ナビゲーション

1. [監視戦略概要](#-監視戦略概要)
2. [監視項目設計](#-監視項目設計)
3. [ログ管理設計](#-ログ管理設計)
4. [アラート設計](#-アラート設計)
5. [ダッシュボード設計](#-ダッシュボード設計)
6. [パフォーマンス監視](#-パフォーマンス監視)
7. [セキュリティ監視](#-セキュリティ監視)
8. [運用プロセス](#-運用プロセス)
9. [自動化戦略](#-自動化戦略)
10. [障害対応](#-障害対応)

## 🎯 監視戦略概要

### 基本情報
- **プロジェクト名**: {PROJECT_NAME}
- **対象システム**: {TARGET_SYSTEM}
- **監視ツール**: {MONITORING_TOOLS}
- **運用チーム**: {OPERATIONS_TEAM}
- **設計者**: {DESIGNER_NAME}
- **設計日**: {DESIGN_DATE}

### 監視目標
```yaml
@monitoring_goals
availability:
  - uptime_target: "{UPTIME_TARGET}%"
  - mttr_target: "{MTTR_TARGET}"
  - mtbf_target: "{MTBF_TARGET}"
performance:
  - response_time_target: "{RESPONSE_TIME_TARGET}ms"
  - throughput_target: "{THROUGHPUT_TARGET}req/s"
  - resource_utilization: "{RESOURCE_UTILIZATION_TARGET}%"
reliability:
  - error_rate_target: "< {ERROR_RATE_TARGET}%"
  - data_accuracy: "{DATA_ACCURACY_TARGET}%"
  - backup_success_rate: "{BACKUP_SUCCESS_TARGET}%"
security:
  - incident_detection_time: "< {DETECTION_TIME_TARGET}"
  - vulnerability_remediation: "< {REMEDIATION_TIME_TARGET}"
```

### 監視レベル定義
| レベル | 対象 | 監視間隔 | データ保持期間 | アラート |
|--------|------|----------|----------------|----------|
| L1: Infrastructure | {L1_TARGETS} | {L1_INTERVAL} | {L1_RETENTION} | {L1_ALERTS} |
| L2: Application | {L2_TARGETS} | {L2_INTERVAL} | {L2_RETENTION} | {L2_ALERTS} |
| L3: Business | {L3_TARGETS} | {L3_INTERVAL} | {L3_RETENTION} | {L3_ALERTS} |
| L4: User Experience | {L4_TARGETS} | {L4_INTERVAL} | {L4_RETENTION} | {L4_ALERTS} |

## 📊 監視項目設計

### インフラストラクチャ監視
```yaml
@infrastructure_monitoring
compute_resources:
  cpu:
    metrics: ["usage_percent", "load_average", "steal_time"]
    thresholds:
      warning: {CPU_WARNING_THRESHOLD}%
      critical: {CPU_CRITICAL_THRESHOLD}%
    collection_interval: {CPU_INTERVAL}s
  memory:
    metrics: ["usage_percent", "available_bytes", "swap_usage"]
    thresholds:
      warning: {MEMORY_WARNING_THRESHOLD}%
      critical: {MEMORY_CRITICAL_THRESHOLD}%
    collection_interval: {MEMORY_INTERVAL}s
  disk:
    metrics: ["usage_percent", "free_space", "iops", "latency"]
    thresholds:
      warning: {DISK_WARNING_THRESHOLD}%
      critical: {DISK_CRITICAL_THRESHOLD}%
    collection_interval: {DISK_INTERVAL}s
network:
  metrics: ["bandwidth_utilization", "packet_loss", "latency", "errors"]
  thresholds:
    warning: {NETWORK_WARNING_THRESHOLD}
    critical: {NETWORK_CRITICAL_THRESHOLD}
  collection_interval: {NETWORK_INTERVAL}s
```

### アプリケーション監視
```yaml
@application_monitoring
web_services:
  http_metrics:
    - response_time: "{RESPONSE_TIME_SLA}ms"
    - status_codes: ["2xx", "4xx", "5xx"]
    - request_rate: "{REQUEST_RATE_BASELINE}req/s"
    - concurrent_users: "{CONCURRENT_USERS_BASELINE}"
  application_metrics:
    - thread_pool_usage: "{THREAD_POOL_THRESHOLD}%"
    - connection_pool_usage: "{CONNECTION_POOL_THRESHOLD}%"
    - garbage_collection: "{GC_THRESHOLD}ms"
    - heap_memory: "{HEAP_MEMORY_THRESHOLD}%"
database:
  performance_metrics:
    - query_response_time: "{DB_RESPONSE_TIME_SLA}ms"
    - connections_active: "{DB_CONNECTIONS_THRESHOLD}"
    - locks_waiting: "{DB_LOCKS_THRESHOLD}"
    - replication_lag: "{REPLICATION_LAG_THRESHOLD}s"
  health_metrics:
    - disk_space: "{DB_DISK_THRESHOLD}%"
    - backup_status: "success/failure"
    - index_fragmentation: "{INDEX_FRAGMENTATION_THRESHOLD}%"
```

### ビジネスメトリクス監視
```yaml
@business_monitoring
key_performance_indicators:
  - user_registrations: "{REGISTRATION_BASELINE}/hour"
  - transaction_volume: "{TRANSACTION_BASELINE}/hour"
  - conversion_rate: "{CONVERSION_RATE_BASELINE}%"
  - revenue_per_hour: "{REVENUE_BASELINE}/hour"
user_experience:
  - page_load_time: "{PAGE_LOAD_SLA}s"
  - user_session_duration: "{SESSION_DURATION_BASELINE}min"
  - bounce_rate: "{BOUNCE_RATE_BASELINE}%"
  - error_rate_user_facing: "{USER_ERROR_RATE_SLA}%"
```

## 📋 ログ管理設計

### ログ収集戦略
```yaml
@log_collection
sources:
  application_logs:
    - format: "{APPLICATION_LOG_FORMAT}"
    - level: "{APPLICATION_LOG_LEVEL}"
    - rotation: "{APPLICATION_LOG_ROTATION}"
    - retention: "{APPLICATION_LOG_RETENTION}"
  web_server_logs:
    - format: "{WEB_SERVER_LOG_FORMAT}"
    - fields: ["{LOG_FIELD_LIST}"]
    - retention: "{WEB_SERVER_LOG_RETENTION}"
  database_logs:
    - slow_query_log: enabled
    - error_log: enabled
    - audit_log: "{AUDIT_LOG_CONFIG}"
    - retention: "{DATABASE_LOG_RETENTION}"
  system_logs:
    - syslog: enabled
    - kernel_logs: enabled
    - security_logs: enabled
    - retention: "{SYSTEM_LOG_RETENTION}"
```

### ログ集約設計
```yaml
@log_aggregation
collection_agents:
  - agent: "{LOG_AGENT}"
    deployment: "{DEPLOYMENT_METHOD}"
    configuration: "{AGENT_CONFIG_PATH}"
central_logging:
  - platform: "{LOGGING_PLATFORM}"
  - storage: "{LOG_STORAGE_BACKEND}"
  - indexing: "{INDEXING_STRATEGY}"
  - search: "{SEARCH_CAPABILITY}"
log_processing:
  - parsing: "{PARSING_RULES}"
  - enrichment: "{ENRICHMENT_RULES}"
  - filtering: "{FILTERING_RULES}"
  - aggregation: "{AGGREGATION_RULES}"
```

### ログ分析設計
| ログタイプ | 分析目的 | 分析ツール | 分析頻度 | アクション |
|------------|----------|------------|----------|------------|
| {LOG_TYPE_1} | {ANALYSIS_PURPOSE} | {ANALYSIS_TOOL} | {FREQUENCY} | {ACTION} |
| {LOG_TYPE_2} | {ANALYSIS_PURPOSE} | {ANALYSIS_TOOL} | {FREQUENCY} | {ACTION} |

### ログセキュリティ
- **アクセス制御**: {LOG_ACCESS_CONTROL}
- **暗号化**: {LOG_ENCRYPTION}
- **改ざん防止**: {LOG_INTEGRITY_PROTECTION}
- **監査ログ**: {AUDIT_LOG_STRATEGY}

## 🚨 アラート設計

### アラート戦略
```yaml
@alert_strategy
severity_levels:
  critical:
    description: "サービス停止・重大な機能障害"
    response_time: "{CRITICAL_RESPONSE_TIME}"
    escalation: "{CRITICAL_ESCALATION}"
    notification: ["{CRITICAL_NOTIFICATION_METHODS}"]
  warning:
    description: "パフォーマンス劣化・軽微な障害"
    response_time: "{WARNING_RESPONSE_TIME}"
    escalation: "{WARNING_ESCALATION}"
    notification: ["{WARNING_NOTIFICATION_METHODS}"]
  info:
    description: "情報提供・予防的通知"
    response_time: "{INFO_RESPONSE_TIME}"
    escalation: "none"
    notification: ["{INFO_NOTIFICATION_METHODS}"]
```

### アラートルール設計
#### インフラストラクチャアラート
```yaml
infrastructure_alerts:
  cpu_high_usage:
    condition: "cpu_usage > {CPU_THRESHOLD}% for {CPU_DURATION}min"
    severity: "warning"
    notification: "{CPU_NOTIFICATION_TARGET}"
    action: "{CPU_AUTO_ACTION}"
  memory_high_usage:
    condition: "memory_usage > {MEMORY_THRESHOLD}% for {MEMORY_DURATION}min"
    severity: "critical"
    notification: "{MEMORY_NOTIFICATION_TARGET}"
    action: "{MEMORY_AUTO_ACTION}"
  disk_space_low:
    condition: "disk_free < {DISK_THRESHOLD}% for {DISK_DURATION}min"
    severity: "warning"
    notification: "{DISK_NOTIFICATION_TARGET}"
    action: "{DISK_AUTO_ACTION}"
```

#### アプリケーションアラート
```yaml
application_alerts:
  high_response_time:
    condition: "avg_response_time > {RESPONSE_TIME_THRESHOLD}ms for {RESPONSE_TIME_DURATION}min"
    severity: "warning"
    notification: "{RESPONSE_TIME_NOTIFICATION_TARGET}"
    action: "{RESPONSE_TIME_AUTO_ACTION}"
  high_error_rate:
    condition: "error_rate > {ERROR_RATE_THRESHOLD}% for {ERROR_RATE_DURATION}min"
    severity: "critical"
    notification: "{ERROR_RATE_NOTIFICATION_TARGET}"
    action: "{ERROR_RATE_AUTO_ACTION}"
  service_down:
    condition: "health_check_failures > {HEALTH_CHECK_THRESHOLD} for {HEALTH_CHECK_DURATION}min"
    severity: "critical"
    notification: "{SERVICE_DOWN_NOTIFICATION_TARGET}"
    action: "{SERVICE_DOWN_AUTO_ACTION}"
```

### アラート通知設計
| 通知方法 | 用途 | 設定 | 制限事項 |
|----------|------|------|----------|
| {NOTIFICATION_METHOD_1} | {PURPOSE} | {CONFIGURATION} | {LIMITATIONS} |
| {NOTIFICATION_METHOD_2} | {PURPOSE} | {CONFIGURATION} | {LIMITATIONS} |

### アラート疲れ対策
- **重複排除**: {DEDUPLICATION_STRATEGY}
- **集約**: {AGGREGATION_STRATEGY}
- **抑制**: {SUPPRESSION_RULES}
- **エスカレーション**: {ESCALATION_STRATEGY}

## 📈 ダッシュボード設計

### ダッシュボード構成
```yaml
@dashboard_design
executive_dashboard:
  audience: "経営陣・ステークホルダー"
  metrics:
    - service_availability: "{AVAILABILITY_DISPLAY}"
    - business_kpis: ["{BUSINESS_KPI_LIST}"]
    - incident_summary: "{INCIDENT_SUMMARY_FORMAT}"
  update_frequency: "{EXECUTIVE_UPDATE_FREQUENCY}"
operations_dashboard:
  audience: "運用チーム"
  metrics:
    - system_health: "{SYSTEM_HEALTH_DISPLAY}"
    - performance_metrics: ["{PERFORMANCE_METRIC_LIST}"]
    - alert_status: "{ALERT_STATUS_DISPLAY}"
    - capacity_metrics: ["{CAPACITY_METRIC_LIST}"]
  update_frequency: "{OPERATIONS_UPDATE_FREQUENCY}"
development_dashboard:
  audience: "開発チーム"
  metrics:
    - application_performance: "{APP_PERFORMANCE_DISPLAY}"
    - error_trends: "{ERROR_TREND_DISPLAY}"
    - deployment_metrics: ["{DEPLOYMENT_METRIC_LIST}"]
  update_frequency: "{DEVELOPMENT_UPDATE_FREQUENCY}"
```

### ダッシュボード設計原則
- **視認性**: {VISIBILITY_PRINCIPLES}
- **関連性**: {RELEVANCE_PRINCIPLES}
- **アクション性**: {ACTIONABILITY_PRINCIPLES}
- **階層化**: {HIERARCHY_PRINCIPLES}

### ダッシュボードメトリクス
| カテゴリ | メトリクス | 表示形式 | 更新頻度 | 閾値表示 |
|----------|------------|----------|----------|----------|
| {CATEGORY_1} | {METRICS_LIST} | {DISPLAY_FORMAT} | {UPDATE_FREQUENCY} | {THRESHOLD_DISPLAY} |
| {CATEGORY_2} | {METRICS_LIST} | {DISPLAY_FORMAT} | {UPDATE_FREQUENCY} | {THRESHOLD_DISPLAY} |

## ⚡ パフォーマンス監視

### パフォーマンス測定戦略
```yaml
@performance_monitoring
response_time_monitoring:
  endpoints:
    - path: "{ENDPOINT_PATH}"
      sla: "{ENDPOINT_SLA}ms"
      measurement: "{MEASUREMENT_METHOD}"
  database_queries:
    - query_type: "{QUERY_TYPE}"
      sla: "{QUERY_SLA}ms"
      measurement: "{MEASUREMENT_METHOD}"
throughput_monitoring:
  application:
    - metric: "requests_per_second"
      baseline: "{RPS_BASELINE}"
      peak_capacity: "{RPS_PEAK_CAPACITY}"
  database:
    - metric: "transactions_per_second"
      baseline: "{TPS_BASELINE}"
      peak_capacity: "{TPS_PEAK_CAPACITY}"
resource_utilization:
  - resource: "cpu"
    optimal_range: "{CPU_OPTIMAL_RANGE}%"
    capacity_planning: "{CPU_CAPACITY_PLANNING}"
  - resource: "memory"
    optimal_range: "{MEMORY_OPTIMAL_RANGE}%"
    capacity_planning: "{MEMORY_CAPACITY_PLANNING}"
```

### 容量計画
```yaml
@capacity_planning
growth_projections:
  - metric: "user_growth"
    current: "{CURRENT_USERS}"
    projected: "{PROJECTED_USERS}"
    timeframe: "{PROJECTION_TIMEFRAME}"
  - metric: "data_growth"
    current: "{CURRENT_DATA_SIZE}"
    projected: "{PROJECTED_DATA_SIZE}"
    timeframe: "{PROJECTION_TIMEFRAME}"
scaling_triggers:
  - metric: "cpu_utilization"
    threshold: "{CPU_SCALING_THRESHOLD}%"
    action: "{CPU_SCALING_ACTION}"
  - metric: "memory_utilization"
    threshold: "{MEMORY_SCALING_THRESHOLD}%"
    action: "{MEMORY_SCALING_ACTION}"
```

## 🔒 セキュリティ監視

### セキュリティ監視項目
```yaml
@security_monitoring
access_monitoring:
  - failed_login_attempts: "{FAILED_LOGIN_THRESHOLD}/min"
  - privilege_escalation: "real-time detection"
  - unauthorized_access: "real-time detection"
  - data_access_patterns: "anomaly detection"
network_monitoring:
  - intrusion_detection: "{IDS_CONFIGURATION}"
  - traffic_anomalies: "{TRAFFIC_ANOMALY_DETECTION}"
  - port_scanning: "real-time detection"
  - ddos_detection: "{DDOS_DETECTION_CONFIGURATION}"
application_security:
  - code_injection: "real-time detection"
  - xss_attempts: "real-time detection"
  - csrf_attempts: "real-time detection"
  - file_upload_anomalies: "real-time detection"
```

### セキュリティアラート
| イベント | 検知方法 | 重要度 | 対応時間 | エスカレーション |
|----------|----------|--------|----------|------------------|
| {SECURITY_EVENT_1} | {DETECTION_METHOD} | {SEVERITY} | {RESPONSE_TIME} | {ESCALATION} |
| {SECURITY_EVENT_2} | {DETECTION_METHOD} | {SEVERITY} | {RESPONSE_TIME} | {ESCALATION} |

### コンプライアンス監視
- **データ保護**: {DATA_PROTECTION_MONITORING}
- **アクセス権監査**: {ACCESS_AUDIT_MONITORING}
- **変更管理**: {CHANGE_MANAGEMENT_MONITORING}
- **証跡管理**: {AUDIT_TRAIL_MONITORING}

## 🔧 運用プロセス

### 日常運用タスク
| タスク | 頻度 | 担当者 | 所要時間 | チェック項目 |
|--------|------|--------|----------|--------------|
| {DAILY_TASK_1} | {FREQUENCY} | {ASSIGNEE} | {DURATION} | {CHECKLIST} |
| {DAILY_TASK_2} | {FREQUENCY} | {ASSIGNEE} | {DURATION} | {CHECKLIST} |

### 定期メンテナンス
```yaml
@maintenance_schedule
weekly_tasks:
  - log_rotation_check: "{LOG_ROTATION_PROCEDURE}"
  - backup_verification: "{BACKUP_VERIFICATION_PROCEDURE}"
  - performance_review: "{PERFORMANCE_REVIEW_PROCEDURE}"
monthly_tasks:
  - capacity_planning_review: "{CAPACITY_REVIEW_PROCEDURE}"
  - security_audit: "{SECURITY_AUDIT_PROCEDURE}"
  - configuration_backup: "{CONFIG_BACKUP_PROCEDURE}"
quarterly_tasks:
  - disaster_recovery_test: "{DR_TEST_PROCEDURE}"
  - monitoring_strategy_review: "{MONITORING_REVIEW_PROCEDURE}"
  - documentation_update: "{DOCUMENTATION_UPDATE_PROCEDURE}"
```

### 運用手順書
#### システム起動手順
```yaml
startup_procedure:
  1_pre_startup_check:
    - infrastructure_health: "{INFRA_HEALTH_CHECK}"
    - dependency_verification: "{DEPENDENCY_CHECK}"
    - configuration_validation: "{CONFIG_VALIDATION}"
  2_startup_sequence:
    - database_startup: "{DB_STARTUP_COMMAND}"
    - application_startup: "{APP_STARTUP_COMMAND}"
    - load_balancer_enable: "{LB_ENABLE_COMMAND}"
  3_post_startup_verification:
    - health_check: "{HEALTH_CHECK_COMMAND}"
    - functional_test: "{FUNCTIONAL_TEST_COMMAND}"
    - monitoring_enable: "{MONITORING_ENABLE_COMMAND}"
```

## 🤖 自動化戦略

### 自動化対象
```yaml
@automation_strategy
monitoring_automation:
  - metric_collection: "automated"
  - alert_processing: "automated"
  - report_generation: "automated"
  - threshold_adjustment: "semi-automated"
response_automation:
  - auto_scaling: "{AUTO_SCALING_CONFIG}"
  - failover: "{FAILOVER_CONFIG}"
  - log_cleanup: "{LOG_CLEANUP_CONFIG}"
  - backup_execution: "{BACKUP_AUTOMATION_CONFIG}"
notification_automation:
  - incident_creation: "automated"
  - status_page_update: "automated"
  - stakeholder_notification: "automated"
  - escalation_management: "automated"
```

### 自動化ツール
| ツール | 用途 | 設定 | 実行スケジュール |
|--------|------|------|------------------|
| {AUTOMATION_TOOL_1} | {PURPOSE} | {CONFIGURATION} | {SCHEDULE} |
| {AUTOMATION_TOOL_2} | {PURPOSE} | {CONFIGURATION} | {SCHEDULE} |

### 自動化の制限と例外
- **手動承認が必要な操作**: {MANUAL_APPROVAL_OPERATIONS}
- **自動化除外項目**: {AUTOMATION_EXCLUSIONS}
- **緊急時の手動介入**: {MANUAL_INTERVENTION_PROCEDURES}

## 🚨 障害対応

### インシデント分類
```yaml
@incident_classification
severity_1:
  definition: "サービス完全停止"
  response_time: "{S1_RESPONSE_TIME}"
  escalation: "{S1_ESCALATION}"
  communication: "{S1_COMMUNICATION}"
severity_2:
  definition: "重要機能の障害"
  response_time: "{S2_RESPONSE_TIME}"
  escalation: "{S2_ESCALATION}"
  communication: "{S2_COMMUNICATION}"
severity_3:
  definition: "軽微な機能障害"
  response_time: "{S3_RESPONSE_TIME}"
  escalation: "{S3_ESCALATION}"
  communication: "{S3_COMMUNICATION}"
```

### 障害対応フロー
```yaml
@incident_response_flow
detection:
  - monitoring_alert: "automated detection"
  - user_report: "manual detection"
  - third_party_notification: "external detection"
initial_response:
  - incident_acknowledgment: "{ACK_TIME_TARGET}"
  - preliminary_assessment: "{ASSESSMENT_TIME_TARGET}"
  - stakeholder_notification: "{NOTIFICATION_TIME_TARGET}"
investigation:
  - root_cause_analysis: "{RCA_PROCESS}"
  - impact_assessment: "{IMPACT_ASSESSMENT_PROCESS}"
  - workaround_implementation: "{WORKAROUND_PROCESS}"
resolution:
  - fix_implementation: "{FIX_IMPLEMENTATION_PROCESS}"
  - verification: "{VERIFICATION_PROCESS}"
  - monitoring: "{POST_RESOLUTION_MONITORING}"
post_incident:
  - post_mortem: "{POST_MORTEM_PROCESS}"
  - improvement_actions: "{IMPROVEMENT_ACTION_PROCESS}"
  - documentation_update: "{DOCUMENTATION_UPDATE_PROCESS}"
```

### 障害対応チーム
| 役割 | 担当者 | 責任範囲 | 連絡方法 |
|------|--------|----------|----------|
| インシデント指揮官 | {INCIDENT_COMMANDER} | {IC_RESPONSIBILITIES} | {IC_CONTACT} |
| 技術リード | {TECH_LEAD} | {TECH_RESPONSIBILITIES} | {TECH_CONTACT} |
| コミュニケーションリード | {COMM_LEAD} | {COMM_RESPONSIBILITIES} | {COMM_CONTACT} |

### エスカレーション基準
- **時間ベース**: {TIME_BASED_ESCALATION}
- **影響度ベース**: {IMPACT_BASED_ESCALATION}
- **技術的複雑さベース**: {COMPLEXITY_BASED_ESCALATION}

---

## 📝 変更履歴

| 日付 | バージョン | 変更者 | 変更内容 |
|------|------------|--------|----------|
| {DATE} | {VERSION} | {AUTHOR} | {CHANGE_DESCRIPTION} |

## 📚 参考資料

- [監視ベストプラクティス]({MONITORING_BEST_PRACTICES_URL})
- [アラート設計ガイド]({ALERT_DESIGN_URL})
- [インシデント対応手順]({INCIDENT_RESPONSE_URL})
- [SREプラクティス]({SRE_PRACTICES_URL})
