# 📚 DocsTemplate

```yaml
@metadata
type: "template-system"
version: "1.0.0"
intent: "AI駆動開発のためのドキュメントテンプレート管理"
capabilities:
  - "ドキュメント自動生成"
  - "AI理解性の最適化"
  - "ドキュメント間の関連性管理"
scope:
  - "プロジェクト概要"
  - "設計仕様"
  - "実装ガイド"
  - "品質管理"
context:
  project: "DocsTemplate"
  parent: null
  children:
    - "./project/*"
    - "./design/*"
    - "./test/*"
    - "./rules/*"
```

## 📑 ナビゲーション

1. [テンプレートの設計思想](#-テンプレートの設計思想)
2. [テンプレート一覧](#-テンプレート一覧)
   - [プロジェクト概要系](#-プロジェクト概要系)
   - [設計・実装系](#-設計実装系)
   - [テスト・品質系](#-テスト品質系)
   - [ルール・規約系](#-ルール規約系)
3. [AIとの対話による成長](#-aiとの対話による成長)
4. [評価指標](#-評価指標)
5. [今後の展開](#-今後の展開)
6. [ライセンス](#-ライセンス)

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
- [README基本テンプレート](./project/readme-template.md)
- [アーキテクチャ概要](./project/architecture-template.md)
- [技術スタック定義](./project/tech-stack-template.md)

### 🔧 設計・実装系
- [コンポーネント設計書](./design/component-template.md)
- [API設計書](./design/api-template.md)
- [データモデル定義](./design/data-model-template.md)

### 🧪 テスト・品質系
- [テスト計画書](./test/test-plan-template.md)
- [品質基準定義](./test/quality-standard-template.md)

### 📋 ルール・規約系
- [コーディング規約](./rules/coding-standard.md)
- [Git運用ルール](./rules/git-workflow.md)
- [ドキュメント規約](./rules/documentation-rules.md)

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

## 🔜 今後の展開

- テンプレート自動生成機能の追加
- AIレビュー支援ツールの統合
- プロジェクト固有のカスタマイズ支援
- マルチ言語対応の拡充

## 📜 ライセンス

このテンプレート集は[MIT License](./LICENSE)の下で公開されています。