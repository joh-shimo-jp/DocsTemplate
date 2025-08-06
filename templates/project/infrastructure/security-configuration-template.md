# セキュリティ設定書テンプレート

```yaml
@metadata
type: "security-configuration"
version: "1.0.0"
intent: "システムセキュリティの設計・実装・運用ガイド"
capabilities:
  - "セキュリティ設計"
  - "アクセス制御"
  - "脆弱性管理"
  - "インシデント対応"
  - "コンプライアンス管理"
scope:
  - "認証・認可"
  - "データ保護"
  - "ネットワークセキュリティ"
  - "アプリケーションセキュリティ"
  - "運用セキュリティ"
context:
  project: "{PROJECT_NAME}"
  compliance_framework: ["{COMPLIANCE_FRAMEWORKS}"]
  threat_model: "{THREAT_MODEL_REFERENCE}"
```

## 📑 ナビゲーション

1. [セキュリティ戦略概要](#-セキュリティ戦略概要)
2. [認証・認可設計](#-認証認可設計)
3. [データ保護設計](#-データ保護設計)
4. [ネットワークセキュリティ](#-ネットワークセキュリティ)
5. [アプリケーションセキュリティ](#-アプリケーションセキュリティ)
6. [インフラストラクチャセキュリティ](#-インフラストラクチャセキュリティ)
7. [脆弱性管理](#-脆弱性管理)
8. [インシデント対応](#-インシデント対応)
9. [コンプライアンス管理](#-コンプライアンス管理)
10. [セキュリティ運用](#-セキュリティ運用)

## 🎯 セキュリティ戦略概要

### 基本情報
- **プロジェクト名**: {PROJECT_NAME}
- **対象システム**: {TARGET_SYSTEM}
- **セキュリティ責任者**: {SECURITY_OFFICER}
- **コンプライアンス要件**: {COMPLIANCE_REQUIREMENTS}
- **脅威モデル**: {THREAT_MODEL}
- **設計者**: {DESIGNER_NAME}
- **設計日**: {DESIGN_DATE}

### セキュリティ目標
```yaml
@security_objectives
confidentiality:
  - data_classification: "{DATA_CLASSIFICATION_LEVELS}"
  - access_control: "{ACCESS_CONTROL_MODEL}"
  - encryption: "{ENCRYPTION_REQUIREMENTS}"
integrity:
  - data_integrity: "{DATA_INTEGRITY_CONTROLS}"
  - system_integrity: "{SYSTEM_INTEGRITY_CONTROLS}"
  - audit_trail: "{AUDIT_TRAIL_REQUIREMENTS}"
availability:
  - uptime_requirement: "{AVAILABILITY_REQUIREMENT}%"
  - disaster_recovery: "{DR_REQUIREMENTS}"
  - business_continuity: "{BC_REQUIREMENTS}"
accountability:
  - audit_logging: "{AUDIT_LOGGING_REQUIREMENTS}"
  - non_repudiation: "{NON_REPUDIATION_CONTROLS}"
  - compliance_reporting: "{COMPLIANCE_REPORTING}"
```

### セキュリティフレームワーク
- **適用フレームワーク**: {SECURITY_FRAMEWORK}
- **リスク評価手法**: {RISK_ASSESSMENT_METHOD}
- **セキュリティ統制**: {SECURITY_CONTROLS}
- **成熟度レベル**: {MATURITY_LEVEL}

### 脅威モデル
```yaml
@threat_model
threat_actors:
  - external_attackers: "{EXTERNAL_THREAT_DESCRIPTION}"
  - malicious_insiders: "{INSIDER_THREAT_DESCRIPTION}"
  - nation_state: "{APT_THREAT_DESCRIPTION}"
  - cybercriminals: "{CYBERCRIME_THREAT_DESCRIPTION}"
attack_vectors:
  - web_application: ["{WEB_ATTACK_VECTORS}"]
  - network: ["{NETWORK_ATTACK_VECTORS}"]
  - social_engineering: ["{SOCIAL_ATTACK_VECTORS}"]
  - physical: ["{PHYSICAL_ATTACK_VECTORS}"]
assets_classification:
  - critical: ["{CRITICAL_ASSETS}"]
  - important: ["{IMPORTANT_ASSETS}"]
  - normal: ["{NORMAL_ASSETS}"]
```

## 🔐 認証・認可設計

### 認証アーキテクチャ
```yaml
@authentication_architecture
identity_providers:
  primary:
    - provider: "{PRIMARY_IDP}"
    - protocol: "{AUTH_PROTOCOL}"
    - mfa_requirement: "{MFA_REQUIREMENT}"
  secondary:
    - provider: "{SECONDARY_IDP}"
    - protocol: "{AUTH_PROTOCOL}"
    - fallback_scenario: "{FALLBACK_SCENARIO}"
authentication_methods:
  - password_policy: "{PASSWORD_POLICY}"
  - multi_factor_authentication: "{MFA_CONFIG}"
  - single_sign_on: "{SSO_CONFIG}"
  - certificate_based: "{CERT_AUTH_CONFIG}"
session_management:
  - session_timeout: "{SESSION_TIMEOUT}"
  - concurrent_sessions: "{CONCURRENT_SESSION_LIMIT}"
  - session_fixation_protection: enabled
  - csrf_protection: enabled
```

### 認可モデル
```yaml
@authorization_model
access_control_model: "{ACCESS_CONTROL_MODEL}" # RBAC/ABAC/etc
roles_definition:
  - role: "{ROLE_NAME}"
    description: "{ROLE_DESCRIPTION}"
    permissions: ["{PERMISSION_LIST}"]
    assignment_criteria: "{ASSIGNMENT_CRITERIA}"
permission_matrix:
  - resource: "{RESOURCE_NAME}"
    actions: ["{ACTION_LIST}"]
    roles: ["{AUTHORIZED_ROLES}"]
access_review:
  - frequency: "{ACCESS_REVIEW_FREQUENCY}"
  - process: "{ACCESS_REVIEW_PROCESS}"
  - approvers: ["{ACCESS_REVIEW_APPROVERS}"]
```

### アカウント管理
| 項目 | 設定 | 実装 | 監査頻度 |
|------|------|------|----------|
| アカウント作成 | {ACCOUNT_CREATION_POLICY} | {CREATION_IMPLEMENTATION} | {CREATION_AUDIT_FREQUENCY} |
| アカウント無効化 | {ACCOUNT_DISABLE_POLICY} | {DISABLE_IMPLEMENTATION} | {DISABLE_AUDIT_FREQUENCY} |
| パスワード管理 | {PASSWORD_POLICY} | {PASSWORD_IMPLEMENTATION} | {PASSWORD_AUDIT_FREQUENCY} |
| 特権アカウント | {PRIVILEGED_ACCOUNT_POLICY} | {PRIVILEGED_IMPLEMENTATION} | {PRIVILEGED_AUDIT_FREQUENCY} |

## 🛡️ データ保護設計

### データ分類
```yaml
@data_classification
classification_levels:
  top_secret:
    - description: "{TOP_SECRET_DESCRIPTION}"
    - examples: ["{TOP_SECRET_EXAMPLES}"]
    - protection_requirements: "{TOP_SECRET_PROTECTION}"
  confidential:
    - description: "{CONFIDENTIAL_DESCRIPTION}"
    - examples: ["{CONFIDENTIAL_EXAMPLES}"]
    - protection_requirements: "{CONFIDENTIAL_PROTECTION}"
  internal:
    - description: "{INTERNAL_DESCRIPTION}"
    - examples: ["{INTERNAL_EXAMPLES}"]
    - protection_requirements: "{INTERNAL_PROTECTION}"
  public:
    - description: "{PUBLIC_DESCRIPTION}"
    - examples: ["{PUBLIC_EXAMPLES}"]
    - protection_requirements: "{PUBLIC_PROTECTION}"
```

### 暗号化戦略
```yaml
@encryption_strategy
data_at_rest:
  - algorithm: "{ENCRYPTION_ALGORITHM}"
  - key_length: "{KEY_LENGTH}"
  - key_management: "{KEY_MANAGEMENT_SYSTEM}"
  - scope: ["{ENCRYPTION_SCOPE}"]
data_in_transit:
  - protocol: "{ENCRYPTION_PROTOCOL}"
  - cipher_suites: ["{CIPHER_SUITES}"]
  - certificate_management: "{CERT_MANAGEMENT}"
  - perfect_forward_secrecy: enabled
data_in_use:
  - application_level_encryption: "{APP_ENCRYPTION}"
  - field_level_encryption: "{FIELD_ENCRYPTION}"
  - tokenization: "{TOKENIZATION_STRATEGY}"
key_management:
  - key_generation: "{KEY_GENERATION_METHOD}"
  - key_rotation: "{KEY_ROTATION_SCHEDULE}"
  - key_escrow: "{KEY_ESCROW_POLICY}"
  - key_destruction: "{KEY_DESTRUCTION_PROCESS}"
```

### データ損失防止 (DLP)
```yaml
@data_loss_prevention
dlp_policies:
  - policy_name: "{DLP_POLICY_NAME}"
    data_types: ["{PROTECTED_DATA_TYPES}"]
    actions: ["{DLP_ACTIONS}"]
    scope: ["{DLP_SCOPE}"]
monitoring:
  - email_monitoring: "{EMAIL_DLP_CONFIG}"
  - web_traffic_monitoring: "{WEB_DLP_CONFIG}"
  - endpoint_monitoring: "{ENDPOINT_DLP_CONFIG}"
  - cloud_storage_monitoring: "{CLOUD_DLP_CONFIG}"
incident_response:
  - detection_threshold: "{DLP_DETECTION_THRESHOLD}"
  - automatic_response: ["{AUTO_RESPONSE_ACTIONS}"]
  - manual_review_process: "{MANUAL_REVIEW_PROCESS}"
```

### バックアップとリカバリ
| データタイプ | バックアップ頻度 | 暗号化 | 保存期間 | リカバリ目標 |
|--------------|------------------|--------|----------|--------------|
| {DATA_TYPE_1} | {BACKUP_FREQUENCY} | {ENCRYPTION_STATUS} | {RETENTION_PERIOD} | {RECOVERY_OBJECTIVE} |
| {DATA_TYPE_2} | {BACKUP_FREQUENCY} | {ENCRYPTION_STATUS} | {RETENTION_PERIOD} | {RECOVERY_OBJECTIVE} |

## 🌐 ネットワークセキュリティ

### ネットワークアーキテクチャ
```yaml
@network_security_architecture
network_segmentation:
  - dmz: "{DMZ_CONFIGURATION}"
  - internal_network: "{INTERNAL_NETWORK_CONFIG}"
  - management_network: "{MANAGEMENT_NETWORK_CONFIG}"
  - backup_network: "{BACKUP_NETWORK_CONFIG}"
firewall_configuration:
  - perimeter_firewall: "{PERIMETER_FW_CONFIG}"
  - internal_firewall: "{INTERNAL_FW_CONFIG}"
  - web_application_firewall: "{WAF_CONFIG}"
  - database_firewall: "{DB_FW_CONFIG}"
intrusion_detection:
  - network_ids: "{NETWORK_IDS_CONFIG}"
  - host_ids: "{HOST_IDS_CONFIG}"
  - behavioral_analysis: "{BEHAVIORAL_IDS_CONFIG}"
```

### ファイアウォール規則
| 方向 | ソース | デスティネーション | プロトコル | ポート | アクション | 備考 |
|------|--------|---------------------|------------|--------|------------|------|
| {DIRECTION} | {SOURCE} | {DESTINATION} | {PROTOCOL} | {PORT} | {ACTION} | {NOTES} |

### VPN設定
```yaml
@vpn_configuration
site_to_site_vpn:
  - encryption: "{VPN_ENCRYPTION}"
  - authentication: "{VPN_AUTH_METHOD}"
  - key_exchange: "{VPN_KEY_EXCHANGE}"
  - tunnel_protocols: ["{VPN_PROTOCOLS}"]
remote_access_vpn:
  - client_software: "{VPN_CLIENT}"
  - authentication: "{CLIENT_AUTH_METHOD}"
  - authorization: "{CLIENT_AUTHORIZATION}"
  - split_tunneling: "{SPLIT_TUNNEL_POLICY}"
vpn_monitoring:
  - connection_logging: enabled
  - traffic_monitoring: enabled
  - performance_monitoring: enabled
```

### DDoS対策
```yaml
@ddos_protection
detection_mechanisms:
  - traffic_analysis: "{TRAFFIC_ANALYSIS_CONFIG}"
  - rate_limiting: "{RATE_LIMITING_CONFIG}"
  - behavioral_analysis: "{BEHAVIORAL_ANALYSIS_CONFIG}"
mitigation_strategies:
  - automatic_mitigation: "{AUTO_MITIGATION_CONFIG}"
  - traffic_shaping: "{TRAFFIC_SHAPING_CONFIG}"
  - upstream_filtering: "{UPSTREAM_FILTERING_CONFIG}"
  - failover_mechanisms: "{FAILOVER_CONFIG}"
```

## 🔒 アプリケーションセキュリティ

### セキュアコーディング
```yaml
@secure_coding_practices
input_validation:
  - validation_framework: "{INPUT_VALIDATION_FRAMEWORK}"
  - sanitization_rules: ["{SANITIZATION_RULES}"]
  - encoding_standards: ["{ENCODING_STANDARDS}"]
output_encoding:
  - context_aware_encoding: enabled
  - xss_prevention: "{XSS_PREVENTION_MEASURES}"
  - content_security_policy: "{CSP_CONFIG}"
authentication_implementation:
  - secure_session_management: "{SESSION_SECURITY_CONFIG}"
  - password_hashing: "{PASSWORD_HASHING_ALGORITHM}"
  - mfa_integration: "{MFA_INTEGRATION_CONFIG}"
error_handling:
  - secure_error_messages: enabled
  - error_logging: "{ERROR_LOGGING_CONFIG}"
  - stack_trace_suppression: enabled
```

### アプリケーションセキュリティテスト
```yaml
@application_security_testing
static_analysis:
  - sast_tools: ["{SAST_TOOLS}"]
  - scan_frequency: "{SAST_FREQUENCY}"
  - integration: "{SAST_CI_INTEGRATION}"
dynamic_analysis:
  - dast_tools: ["{DAST_TOOLS}"]
  - scan_frequency: "{DAST_FREQUENCY}"
  - test_environment: "{DAST_ENVIRONMENT}"
interactive_analysis:
  - iast_tools: ["{IAST_TOOLS}"]
  - runtime_protection: "{RASP_CONFIG}"
manual_testing:
  - penetration_testing: "{PENTEST_SCHEDULE}"
  - code_review: "{CODE_REVIEW_PROCESS}"
```

### API セキュリティ
```yaml
@api_security
authentication:
  - api_key_management: "{API_KEY_CONFIG}"
  - oauth_implementation: "{OAUTH_CONFIG}"
  - jwt_configuration: "{JWT_CONFIG}"
authorization:
  - scope_based_access: "{SCOPE_CONFIG}"
  - rate_limiting: "{API_RATE_LIMITING}"
  - quota_management: "{API_QUOTA_CONFIG}"
data_protection:
  - request_validation: "{REQUEST_VALIDATION}"
  - response_filtering: "{RESPONSE_FILTERING}"
  - data_masking: "{API_DATA_MASKING}"
monitoring:
  - api_gateway_logging: "{API_GATEWAY_LOGS}"
  - anomaly_detection: "{API_ANOMALY_DETECTION}"
  - security_analytics: "{API_SECURITY_ANALYTICS}"
```

## 🏗️ インフラストラクチャセキュリティ

### サーバーセキュリティ
```yaml
@server_security
hardening:
  - os_hardening: "{OS_HARDENING_STANDARD}"
  - service_minimization: "{SERVICE_MINIMIZATION}"
  - patch_management: "{PATCH_MANAGEMENT_PROCESS}"
access_control:
  - ssh_configuration: "{SSH_CONFIG}"
  - sudo_configuration: "{SUDO_CONFIG}"
  - service_accounts: "{SERVICE_ACCOUNT_CONFIG}"
monitoring:
  - file_integrity_monitoring: "{FIM_CONFIG}"
  - process_monitoring: "{PROCESS_MONITORING_CONFIG}"
  - log_monitoring: "{LOG_MONITORING_CONFIG}"
```

### コンテナセキュリティ
```yaml
@container_security
image_security:
  - base_image_policy: "{BASE_IMAGE_POLICY}"
  - vulnerability_scanning: "{CONTAINER_SCANNING_CONFIG}"
  - image_signing: "{IMAGE_SIGNING_CONFIG}"
runtime_security:
  - container_isolation: "{CONTAINER_ISOLATION_CONFIG}"
  - resource_limits: "{RESOURCE_LIMITS_CONFIG}"
  - network_policies: "{CONTAINER_NETWORK_POLICIES}"
orchestration_security:
  - kubernetes_rbac: "{K8S_RBAC_CONFIG}"
  - pod_security_policies: "{POD_SECURITY_POLICIES}"
  - network_segmentation: "{K8S_NETWORK_SEGMENTATION}"
```

### クラウドセキュリティ
```yaml
@cloud_security
identity_and_access:
  - iam_policies: "{CLOUD_IAM_POLICIES}"
  - mfa_enforcement: "{CLOUD_MFA_CONFIG}"
  - privileged_access_management: "{CLOUD_PAM_CONFIG}"
data_protection:
  - encryption_at_rest: "{CLOUD_ENCRYPTION_CONFIG}"
  - key_management_service: "{CLOUD_KMS_CONFIG}"
  - backup_encryption: "{CLOUD_BACKUP_ENCRYPTION}"
network_security:
  - vpc_configuration: "{VPC_CONFIG}"
  - security_groups: "{SECURITY_GROUP_CONFIG}"
  - network_access_control: "{NETWORK_ACL_CONFIG}"
monitoring:
  - cloudtrail_logging: "{CLOUDTRAIL_CONFIG}"
  - security_monitoring: "{CLOUD_SECURITY_MONITORING}"
  - compliance_monitoring: "{CLOUD_COMPLIANCE_MONITORING}"
```

## 🔍 脆弱性管理

### 脆弱性管理プロセス
```yaml
@vulnerability_management
discovery:
  - vulnerability_scanning: "{VULN_SCANNING_SCHEDULE}"
  - penetration_testing: "{PENTEST_SCHEDULE}"
  - threat_intelligence: "{THREAT_INTEL_SOURCES}"
assessment:
  - risk_scoring: "{RISK_SCORING_METHOD}"
  - impact_analysis: "{IMPACT_ANALYSIS_PROCESS}"
  - exploitability_assessment: "{EXPLOITABILITY_ASSESSMENT}"
prioritization:
  - critical_vulnerabilities: "{CRITICAL_VULN_SLA}"
  - high_vulnerabilities: "{HIGH_VULN_SLA}"
  - medium_vulnerabilities: "{MEDIUM_VULN_SLA}"
  - low_vulnerabilities: "{LOW_VULN_SLA}"
remediation:
  - patch_management: "{PATCH_MANAGEMENT_PROCESS}"
  - workaround_implementation: "{WORKAROUND_PROCESS}"
  - risk_acceptance: "{RISK_ACCEPTANCE_PROCESS}"
```

### 脆弱性スキャン設定
| スキャンタイプ | 対象 | 頻度 | ツール | 報告先 |
|----------------|------|------|--------|--------|
| {SCAN_TYPE_1} | {SCAN_TARGET} | {SCAN_FREQUENCY} | {SCAN_TOOL} | {REPORT_RECIPIENT} |
| {SCAN_TYPE_2} | {SCAN_TARGET} | {SCAN_FREQUENCY} | {SCAN_TOOL} | {REPORT_RECIPIENT} |

### パッチ管理
```yaml
@patch_management
patch_categories:
  - security_patches: "{SECURITY_PATCH_SLA}"
  - critical_patches: "{CRITICAL_PATCH_SLA}"
  - regular_patches: "{REGULAR_PATCH_SLA}"
testing_process:
  - test_environment: "{PATCH_TEST_ENVIRONMENT}"
  - testing_procedures: "{PATCH_TESTING_PROCEDURES}"
  - rollback_procedures: "{PATCH_ROLLBACK_PROCEDURES}"
deployment:
  - deployment_windows: ["{PATCH_DEPLOYMENT_WINDOWS}"]
  - approval_process: "{PATCH_APPROVAL_PROCESS}"
  - emergency_patching: "{EMERGENCY_PATCH_PROCESS}"
```

## 🚨 インシデント対応

### インシデント分類
```yaml
@incident_classification
security_incidents:
  category_1_critical:
    - description: "データ漏洩・システム侵害"
    - response_time: "{CAT1_RESPONSE_TIME}"
    - escalation: "{CAT1_ESCALATION}"
  category_2_high:
    - description: "重要システムの機能停止"
    - response_time: "{CAT2_RESPONSE_TIME}"
    - escalation: "{CAT2_ESCALATION}"
  category_3_medium:
    - description: "セキュリティポリシー違反"
    - response_time: "{CAT3_RESPONSE_TIME}"
    - escalation: "{CAT3_ESCALATION}"
  category_4_low:
    - description: "軽微なセキュリティイベント"
    - response_time: "{CAT4_RESPONSE_TIME}"
    - escalation: "{CAT4_ESCALATION}"
```

### インシデント対応プロセス
```yaml
@incident_response_process
preparation:
  - incident_response_team: ["{IR_TEAM_MEMBERS}"]
  - response_procedures: "{IR_PROCEDURES}"
  - communication_plan: "{IR_COMMUNICATION_PLAN}"
  - tools_and_resources: ["{IR_TOOLS}"]
detection_and_analysis:
  - detection_mechanisms: ["{DETECTION_MECHANISMS}"]
  - initial_analysis: "{INITIAL_ANALYSIS_PROCESS}"
  - incident_classification: "{CLASSIFICATION_PROCESS}"
  - evidence_collection: "{EVIDENCE_COLLECTION_PROCESS}"
containment_eradication_recovery:
  - containment_strategy: "{CONTAINMENT_STRATEGY}"
  - eradication_procedures: "{ERADICATION_PROCEDURES}"
  - recovery_procedures: "{RECOVERY_PROCEDURES}"
  - system_restoration: "{SYSTEM_RESTORATION_PROCESS}"
post_incident_activity:
  - lessons_learned: "{LESSONS_LEARNED_PROCESS}"
  - report_generation: "{INCIDENT_REPORTING}"
  - process_improvement: "{PROCESS_IMPROVEMENT}"
```

### フォレンジック手順
```yaml
@forensics_procedures
evidence_preservation:
  - chain_of_custody: "{CHAIN_OF_CUSTODY_PROCESS}"
  - evidence_integrity: "{EVIDENCE_INTEGRITY_MEASURES}"
  - documentation: "{FORENSIC_DOCUMENTATION}"
data_collection:
  - live_system_analysis: "{LIVE_ANALYSIS_PROCEDURES}"
  - disk_imaging: "{DISK_IMAGING_PROCEDURES}"
  - memory_analysis: "{MEMORY_ANALYSIS_PROCEDURES}"
  - network_analysis: "{NETWORK_ANALYSIS_PROCEDURES}"
analysis_and_reporting:
  - forensic_tools: ["{FORENSIC_TOOLS}"]
  - analysis_methodology: "{ANALYSIS_METHODOLOGY}"
  - reporting_format: "{FORENSIC_REPORT_FORMAT}"
```

## 📋 コンプライアンス管理

### 適用法規制
```yaml
@compliance_requirements
regulations:
  - regulation_name: "{REGULATION_NAME}"
    applicability: "{APPLICABILITY}"
    key_requirements: ["{KEY_REQUIREMENTS}"]
    compliance_status: "{COMPLIANCE_STATUS}"
standards:
  - standard_name: "{STANDARD_NAME}"
    version: "{STANDARD_VERSION}"
    certification_status: "{CERTIFICATION_STATUS}"
    next_audit: "{NEXT_AUDIT_DATE}"
frameworks:
  - framework_name: "{FRAMEWORK_NAME}"
    implementation_level: "{IMPLEMENTATION_LEVEL}"
    gap_analysis: "{GAP_ANALYSIS_RESULTS}"
```

### コンプライアンス統制
| 統制項目 | 要件 | 実装状況 | 証跡 | 次回レビュー |
|----------|------|----------|------|--------------|
| {CONTROL_ID_1} | {CONTROL_REQUIREMENT} | {IMPLEMENTATION_STATUS} | {EVIDENCE} | {NEXT_REVIEW} |
| {CONTROL_ID_2} | {CONTROL_REQUIREMENT} | {IMPLEMENTATION_STATUS} | {EVIDENCE} | {NEXT_REVIEW} |

### 監査対応
```yaml
@audit_management
internal_audits:
  - frequency: "{INTERNAL_AUDIT_FREQUENCY}"
  - scope: ["{INTERNAL_AUDIT_SCOPE}"]
  - auditors: ["{INTERNAL_AUDITORS}"]
external_audits:
  - frequency: "{EXTERNAL_AUDIT_FREQUENCY}"
  - certification_body: "{CERTIFICATION_BODY}"
  - audit_scope: ["{EXTERNAL_AUDIT_SCOPE}"]
audit_preparation:
  - evidence_collection: "{EVIDENCE_COLLECTION_PROCESS}"
  - documentation_review: "{DOCUMENTATION_REVIEW_PROCESS}"
  - interview_preparation: "{INTERVIEW_PREPARATION}"
```

## 🔧 セキュリティ運用

### セキュリティ運用センター (SOC)
```yaml
@security_operations_center
staffing:
  - soc_manager: "{SOC_MANAGER}"
  - security_analysts: ["{SECURITY_ANALYSTS}"]
  - incident_responders: ["{INCIDENT_RESPONDERS}"]
  - coverage: "{SOC_COVERAGE_HOURS}"
tools_and_technologies:
  - siem_platform: "{SIEM_PLATFORM}"
  - threat_intelligence: "{THREAT_INTEL_PLATFORM}"
  - orchestration_tools: "{SOAR_PLATFORM}"
  - forensic_tools: ["{FORENSIC_TOOLS}"]
processes:
  - monitoring_procedures: "{MONITORING_PROCEDURES}"
  - escalation_procedures: "{ESCALATION_PROCEDURES}"
  - reporting_procedures: "{REPORTING_PROCEDURES}"
```

### セキュリティメトリクス
```yaml
@security_metrics
technical_metrics:
  - vulnerability_management_metrics:
    - mean_time_to_patch: "{MTTP_TARGET}"
    - vulnerability_density: "{VULN_DENSITY_TARGET}"
    - patch_compliance_rate: "{PATCH_COMPLIANCE_TARGET}%"
  - incident_response_metrics:
    - mean_time_to_detection: "{MTTD_TARGET}"
    - mean_time_to_response: "{MTTR_TARGET}"
    - incident_containment_rate: "{CONTAINMENT_RATE_TARGET}%"
business_metrics:
  - security_investment_roi: "{SECURITY_ROI_TARGET}"
  - compliance_cost: "{COMPLIANCE_COST_BUDGET}"
  - business_impact_reduction: "{IMPACT_REDUCTION_TARGET}%"
```

### セキュリティ意識向上
```yaml
@security_awareness
training_program:
  - general_security_awareness: "{GENERAL_TRAINING_FREQUENCY}"
  - role_specific_training: "{ROLE_SPECIFIC_TRAINING}"
  - phishing_simulation: "{PHISHING_SIM_FREQUENCY}"
  - incident_response_training: "{IR_TRAINING_FREQUENCY}"
communication:
  - security_newsletters: "{NEWSLETTER_FREQUENCY}"
  - security_alerts: "{ALERT_COMMUNICATION_METHOD}"
  - policy_updates: "{POLICY_UPDATE_COMMUNICATION}"
measurement:
  - training_completion_rate: "{TRAINING_COMPLETION_TARGET}%"
  - phishing_click_rate: "{PHISHING_CLICK_TARGET}%"
  - security_incident_reporting: "{INCIDENT_REPORTING_TARGET}"
```

### 定期セキュリティ活動
| 活動 | 頻度 | 担当者 | 成果物 | 次回実施日 |
|------|------|--------|--------|------------|
| {SECURITY_ACTIVITY_1} | {FREQUENCY} | {RESPONSIBLE_PARTY} | {DELIVERABLES} | {NEXT_DATE} |
| {SECURITY_ACTIVITY_2} | {FREQUENCY} | {RESPONSIBLE_PARTY} | {DELIVERABLES} | {NEXT_DATE} |

---

## 📝 変更履歴

| 日付 | バージョン | 変更者 | 変更内容 |
|------|------------|--------|----------|
| {DATE} | {VERSION} | {AUTHOR} | {CHANGE_DESCRIPTION} |

## 📚 参考資料

- [セキュリティフレームワーク]({SECURITY_FRAMEWORK_URL})
- [脅威インテリジェンス]({THREAT_INTEL_URL})
- [セキュリティベストプラクティス]({SECURITY_BEST_PRACTICES_URL})
- [コンプライアンスガイド]({COMPLIANCE_GUIDE_URL})
- [インシデント対応ガイド]({INCIDENT_RESPONSE_GUIDE_URL})
