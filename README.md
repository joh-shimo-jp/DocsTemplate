# 📚 DocsTemplate

```yaml
@metadata
type: "template-system"
version: "1.0.0"
i#### 機能・インフラドキュメント
- [機能開発統合テンプレート](./templates/project/feature/) - UI・設計・テスト
- [インフラ設計書](./templates/project/infrastructure/) - クラウド・CI/CD・運用

### 🧪 品質管理系
- [品質基準定義](./templates/test/quality-standard-template.md)

### 📋 ルール・規約系
- [コーディング規約](./templates/rules/coding-standard.md)
- [Git運用ルール](./templates/rules/git-workflow.md)
- [ドキュメント規約](./templates/rules/documentation-rules.md)ュメントテンプレート管理"
capabilities:
  - "ドキュメント自動生成"
  - "AI理解性の最適化"
  - "ドキュメント間の関連性管理"
scope:
  - "プロジェクト概要"
  - "設計仕様"
  - "実装ガイド"
  - "品質管理"
  - "インフラ・CI/CD"
context:
  project: "DocsTemplate"
  parent: null
  children:
    - "./project/*"
    - "./design/*"
    - "./test/*"
    - "./rules/*"
    - "./infrastructure/*"
```

## 📑 ナビゲーション

1. [テンプレートの設計思想](#-テンプレートの設計思想)
2. [テンプレート一覧](#-テンプレート一覧)
   - [プロジェクト概要系](#-プロジェクト概要系)
   - [設計・実装系](#-設計実装系)
   - [テスト・品質系](#-テスト品質系)
   - [ルール・規約系](#-ルール規約系)
   - [インフラ・CI/CD系](#️-インフラcicd系)
3. [AIとの対話による成長](#-aiとの対話による成長)
4. [評価指標](#-評価指標)
5. [AI制約とガイドライン](#-ai制約とガイドライン)
6. [今後の展開](#-今後の展開)
7. [ライセンス](#-ライセンス)

## 🎯 テンプレートの設計思想

```yaml
@design_principles
core_concepts:
  ai_understanding:
    description: "AIが文脈を理解し、適切な提案や更新ができる構造"
    implementation:
      - "メタデータDSLの活用"
      - "文脈情報の明示的な記述"
      - "関連性の構造化"
  
  hierarchical_detail:
    description: "概要から詳細まで、階層的に情報を整理"
    levels:
      - "L1: 概要・目的"
      - "L2: 構造・仕様"
      - "L3: 実装詳細"
  
  extensibility:
    description: "プロジェクトの成長に合わせて自然に発展できる構造"
    mechanisms:
      - "バージョン管理"
      - "変更履歴"
      - "拡張ポイントの明示"

- **AI理解性**: AIが文脈を理解し、適切な提案や更新ができる構造
- **段階的詳細化**: 概要から詳細まで、階層的に情報を整理
- **柔軟な拡張性**: プロジェクトの成長に合わせて自然に発展できる構造
- **相互参照の容易さ**: ドキュメント間の関連性を明確に表現
- **メンテナンス性**: 更新・レビュー・履歴管理のしやすさ

## 📑 テンプレート一覧

### 📘 プロジェクト概要系
- [READMEテンプレート](./templates/project/readme-template.md)
- [アーキテクチャ概要](./templates/project/architecture-template.md)
- [技術スタック定義](./templates/project/tech-stack-template.md)
- [フロントエンド特化README](./templates/project/frontend-readme-template.md)
- [バックエンド特化README](./templates/project/backend-readme-template.md)
- [AI/ML特化README](./templates/project/ai-ml-readme-template.md)

#### 機能・インフラドキュメント
- [機能企画・要求仕様書](./templates/project/feature/)
- [インフラ設計書](./templates/project/infrastructure/)

### 🔧 システム設計系
- [API設計書](./templates/design/api-template.md)

### � 機能開発系
- [機能開発テンプレート総合](./templates/feature/)
- [UI設計テンプレート](./templates/feature/ui/)
- [機能設計テンプレート](./templates/feature/design/)
- [機能テストテンプレート](./templates/feature/test/)

### 🧪 品質管理系
- [品質基準定義](./templates/test/quality-standard-template.md)

### 📋 ルール・規約系
- [コーディング規約](./templates/rules/coding-standard.md)
- [Git運用ルール](./templates/rules/git-workflow.md)
- [ドキュメント規約](./templates/rules/documentation-rules.md)

## 🌿 AIとの対話による成長

1. **理解の深化**
   - AIによる文脈理解の継続的な改善
   - 対話履歴からの学習と適応
   - パターンの抽出と最適化

2. **フィードバックループ**
   - 実装結果の分析
   - ユースケースの蓄積
   - 改善提案の自動生成

## 📊 評価指標

| 観点 | 評価基準 | 確認方法 |
|------|----------|----------|
| AI理解性 | AIが文脈を正しく解釈できる | AI対話テストの成功率 |
| 保守性 | 更新の容易さ、一貫性の維持 | レビュー時間、修正回数 |
| 活用度 | テンプレートの使用頻度 | 使用統計、参照回数 |
| 拡張性 | カスタマイズの柔軟さ | カスタマイズ事例数 |

## 🤖 AI制約とガイドライン

DocsTemplateでは、AIがテンプレートを適切に理解・生成・更新できるよう、専用の制約定義を設けています。

### AI制約ファイル
- **制約定義**: [ai-constraints.yaml](./ai-constraints.yaml)
- **目的**: テンプレート品質の一貫性確保とAI理解性の最適化
- **適用範囲**: すべてのテンプレート作業（作成・更新・カスタマイズ）

### 重要な制約事項

```yaml
@ai_mandatory_rules
template_quality_standards:
  - ai_readability: "95%以上"
  - metadata_completeness: "100%"
  - structure_compliance: "100%"
  - placeholder_consistency: "100%"

design_principles:
  - ai_understanding_optimization: "AI理解性を最優先"
  - hierarchical_detail: "L1概要→L2構造→L3実装"
  - consistency_maintenance: "既存テンプレートとの統一性"
  - extensibility_assurance: "拡張性の確保"
```

### AIによるテンプレート作業時の必須手順

1. **📖 理念理解**: DocsTemplate設計思想の確認
2. **🎯 品質基準**: AI理解性・構造準拠・完全性の確認
3. **📋 構造確認**: 必須セクション・プレースホルダー形式の把握
4. **🔄 整合性**: 関連テンプレートとの一貫性確認
5. **✅ 品質検証**: 制約遵守状況の最終確認

**⚠️ 重要**: すべてのテンプレート関連作業前に [`ai-constraints.yaml`](./ai-constraints.yaml) を参照し、制約事項を理解してから作業を開始してください。

## 🔜 今後の展開

- テンプレート自動生成機能の追加
- AIレビュー支援ツールの統合
- プロジェクト固有のカスタマイズ支援
- マルチ言語対応の拡充

## 📜 ライセンス

このテンプレート集は[MIT License](./LICENSE)の下で公開されています。