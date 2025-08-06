# Project Feature Templates

このディレクトリには、機能開発に関する包括的なテンプレートが含まれています。

## 📁 テンプレート構成

### 🎨 [UI Templates](./ui/)
ユーザーインターフェース設計用テンプレート
- コンポーネント設計
- レイアウト設計
- ワイヤーフレーム

### 🔧 [Design Templates](./design/)
機能設計・実装用テンプレート
- API設計書
- 機能仕様書
- データフロー設計
- コンポーネント設計
- データモデル定義

### 🧪 [Test Templates](./test/)
機能テスト用テンプレート
- テスト計画書
- テストケース定義

## 🚀 使用方法

### 機能開発開始時
```bash
# 機能開発の全要素（UI・設計・テスト）を一括取得
cp -r {DocsTemplateWorkspace}/templates/project/feature {target-project}/docs/{feature-name}
```

### 個別テンプレート使用時
```bash
# UI設計のみ
cp -r {DocsTemplateWorkspace}/templates/project/feature/ui {target-project}/docs/ui-design

# 設計テンプレートのみ
cp -r {DocsTemplateWorkspace}/templates/project/feature/design {target-project}/docs/design

# テストテンプレートのみ
cp -r {DocsTemplateWorkspace}/templates/project/feature/test {target-project}/docs/test
```

### 段階的な作業フロー
1. **L1: 概要定義** - 機能の目的・スコープを明確化
2. **L2: 構造設計** - UI/Design/Testで詳細設計
3. **L3: 実装詳細** - 具体的な実装仕様の策定

### カスタマイズ
- プロジェクト固有の要件に応じてテンプレートを調整
- プレースホルダー（`{feature-name}`等）を実際の値に置換
- 不要なセクションは削除、必要なセクションは追加

## 🔗 関連リソース

- **[Project Templates](../)** - その他のプロジェクトドキュメント
- **[Project Infrastructure Templates](../infrastructure/)** - インフラ設計テンプレート
- **[Quality Standards Templates](../../test/)** - 品質管理テンプレート
- **[Rules Templates](../../rules/)** - 開発規約・ルール
- **[AI制約定義](../../../ai-constraints.yaml)** - AI作業時の制約事項

## 💡 ベストプラクティス

### ドキュメント作成時
- AI制約に従った構造の維持
- メタデータの適切な記載
- 明確なナビゲーション構造

### チーム協働時
- 統一されたテンプレート使用
- 定期的なレビューとアップデート
- 関連ドキュメントとの整合性確保
