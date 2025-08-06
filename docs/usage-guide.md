# DocsTemplate 使用ガイド

このガイドでは、DocsTemplateの効果的な使用方法について説明します。

## 🎯 基本的な使用フロー

### 1. テンプレート選択
```yaml
selection_criteria:
  document_type: "作成したいドキュメントの種類"
  project_phase: "プロジェクトの段階（企画・設計・実装・運用）"
  complexity: "要求される詳細度（簡易・標準・詳細）"
```

**カテゴリ別選択指針**:
- **Project系**: プロジェクト開始時、概要整理時
- **Design系**: 詳細設計フェーズ、API・コンポーネント設計時
- **Feature Design系**: 新機能開発開始時
- **Infrastructure系**: インフラ構築・運用設計時
- **Test系**: テスト計画策定時
- **Rules系**: チーム立ち上げ・規約整備時

### 2. テンプレートコピー・配置
```bash
# 基本的なコピー手順
cp -r {DocsTemplate}/templates/{category}/{template} {target-location}

# 例：フィーチャー設計テンプレートの使用
cp -r ./DocsTemplate/templates/feature-design/template ./project/docs/new-feature
```

### 3. カスタマイズ
#### 必須置換項目
- `{project-name}` → 実際のプロジェクト名
- `{feature-name}` → 機能名
- `{Feature Name}` → 日本語機能名
- `{version}` → バージョン情報
- メタデータセクションの更新

#### AI制約準拠確認
```yaml
@mandatory_check
metadata_completeness: "メタデータの完全性"
structure_compliance: "テンプレート構造の遵守"
ai_readability: "AI理解可能性"
navigation_consistency: "ナビゲーションの一貫性"
```

## 🔧 高度な使用方法

### プロジェクト固有カスタマイズ
1. **セクション追加・削除**
   - プロジェクト要件に応じた調整
   - 必須セクションは維持

2. **メタデータ拡張**
   - プロジェクト固有の属性追加
   - AI理解を助ける context 情報

3. **テンプレート組み合わせ**
   - 複数テンプレートの統合使用
   - 大規模プロジェクトでの階層化

### AI連携最適化
```yaml
@ai_optimization_tips
clear_context: "明確な文脈情報の提供"
structured_metadata: "構造化されたメタデータ"
consistent_terminology: "一貫した用語使用"
explicit_relationships: "明示的な関連性表現"
```

## 🚨 注意事項・制約

### 必須制約
- **AI制約遵守**: [ai-constraints.yaml](../ai-constraints.yaml)の完全遵守
- **構造維持**: 基本的なテンプレート構造の保持
- **メタデータ必須**: @metadata セクションの必須記載

### 品質基準
- **AI理解性**: 95%以上
- **構造準拠性**: 100%
- **メタデータ完全性**: 100%

## 🔄 更新・メンテナンス

### テンプレート更新時の手順
1. DocsTemplateの最新版取得
2. 既存カスタマイズとの差分確認
3. 新機能・改善の適用検討
4. 移行テスト実行

### 品質チェック
```bash
# 構造チェック（例）
validate_template_structure.py {document-path}

# AI理解性チェック（例）
ai_readability_test.py {document-path}
```

## 📞 サポート・トラブルシューティング

### よくある問題
1. **メタデータ形式エラー**: YAML形式の確認
2. **ナビゲーション不整合**: リンク先の存在確認
3. **AI理解性低下**: 文脈情報の明確化

### 改善提案
新しいテンプレート提案や既存テンプレートの改善案は、DocsTemplateリポジトリのIssueとして提出してください。
