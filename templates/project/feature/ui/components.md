# {Feature Name} UIコンポーネント仕様テンプレート

```yaml
@metadata
type: "ui_component_template"
version: "1.0.0"
intent: "{Feature Name}の個別UIコンポーネント詳細仕様定義テンプレート"
context:
  project: "{project_name}"
  feature: "{feature_name}"
  layer: "ui_component"
  parent: "./README.md"
  children: []
capabilities:
  - "コンポーネント仕様の構造化定義"
  - "プロパティ・イベント管理"
  - "状態管理設計"
  - "アクセシビリティ対応"
  - "テスト仕様定義"
scope:
  - "個別コンポーネント設計"
  - "コンポーネント間の関係性"
  - "状態管理仕様"
  - "ユーザビリティ設計"
```

## 📑 ナビゲーション

### UI設計ドキュメント
- **[UI設計概要](./README.md)** - UI設計全体ナビゲーション
- **[レイアウト設計](./layouts.md)** - 画面レイアウト仕様
- **[ワイヤーフレーム](./wireframes/)** - モックアップ・ビジュアルデザイン

### 関連リソース
- **[機能設計](../design/README.md)** - 機能詳細設計
- **[テスト設計](../test/)** - UIテスト計画
- **[機能概要](../README.md)** - 機能全体情報

個別UIコンポーネントの詳細仕様を定義します。

## 📋 コンポーネント一覧

### 主要コンポーネント

| コンポーネント | 用途 | 依存関係 | 状態 |
|---------------|------|----------|------|
| {Component1} | {用途説明} | {依存コンポーネント} | 🔄設計中 |
| {Component2} | {用途説明} | {依存コンポーネント} | ✅完了 |
| {Component3} | {用途説明} | {依存コンポーネント} | 📝実装待ち |

## 🧩 コンポーネント詳細仕様

### {Component1}

```yaml
@component: {component_name_1}
description: "{コンポーネントの説明}"
category: "{カテゴリ}" # primary, secondary, utility
props:
  {prop1}:
    type: {type}
    required: {true/false}
    default: {default_value}
    description: "{説明}"
  {prop2}:
    type: {type}
    required: {true/false}
    description: "{説明}"
state:
  {state1}:
    type: {type}
    description: "{状態の説明}"
    initial_value: {initial_value}
  {state2}:
    type: {type}
    description: "{状態の説明}"
events:
  - {event1}: "{イベントの説明}"
  - {event2}: "{イベントの説明}"
accessibility:
  - "{アクセシビリティ要件1}"
  - "{アクセシビリティ要件2}"
```

#### 使用例

```dart
{Component1}(
  {prop1}: {value1},
  {prop2}: {value2},
  on{Event1}: () {
    // イベントハンドラー
  },
)
```

#### スタイル仕様

```dart
@style_specs
colors:
  primary: {color_code}
  secondary: {color_code}
  text: {color_code}
typography:
  font_family: {font_family}
  font_size: {size}
  font_weight: {weight}
spacing:
  padding: {padding_value}
  margin: {margin_value}
border:
  radius: {radius_value}
  width: {width_value}
  color: {color_code}
```

### {Component2}

```yaml
@component: {component_name_2}
description: "{コンポーネントの説明}"
category: "{カテゴリ}"
props:
  {prop1}:
    type: {type}
    required: {true/false}
    description: "{説明}"
state:
  {state1}:
    type: {type}
    description: "{状態の説明}"
events:
  - {event1}: "{イベントの説明}"
```

## 🎨 デザインシステム

### カラーパレット

```yaml
@color_palette
primary:
  main: "{color_code}"
  light: "{color_code}"
  dark: "{color_code}"
secondary:
  main: "{color_code}"
  light: "{color_code}"
  dark: "{color_code}"
semantic:
  success: "{color_code}"
  warning: "{color_code}"
  error: "{color_code}"
  info: "{color_code}"
```

### タイポグラフィ

```yaml
@typography
heading:
  h1: "{font_size}/{line_height}"
  h2: "{font_size}/{line_height}"
  h3: "{font_size}/{line_height}"
body:
  large: "{font_size}/{line_height}"
  medium: "{font_size}/{line_height}"
  small: "{font_size}/{line_height}"
caption: "{font_size}/{line_height}"
```

## 📱 レスポンシブ対応

### ブレイクポイント

| サイズ | 幅 | 対応 |
|--------|----|----- |
| Small | ~768px | {対応内容} |
| Medium | 768px~1024px | {対応内容} |
| Large | 1024px~ | {対応内容} |

### コンポーネント調整

```yaml
@responsive_adjustments
{Component1}:
  small: "{調整内容}"
  medium: "{調整内容}"
  large: "{調整内容}"
{Component2}:
  small: "{調整内容}"
  medium: "{調整内容}"
```

## 🧪 テスト仕様

### ユニットテスト

```dart
// {Component1} テスト例
testWidgets('{Component1} displays correctly', (tester) async {
  await tester.pumpWidget({Component1}(
    {prop1}: {test_value},
    {prop2}: {test_value},
  ));
  
  expect(find.text('{expected_text}'), findsOneWidget);
  expect(find.byType({ComponentType}), findsOneWidget);
});
```

### ビジュアルテスト

- {ビジュアルテスト項目1}
- {ビジュアルテスト項目2}
- {ビジュアルテスト項目3}

## 🔗 関連ドキュメント

- **[UI概要](./README.md)** - UI設計概要
- **[レイアウト設計](./layouts.md)** - 画面レイアウト
- **[ワイヤーフレーム](./wireframes/)** - ビジュアルデザイン
- **[機能設計](../README.md)** - 機能全体設計
- **[共通UI](../../common-ui/README.md)** - 共通コンポーネント

---

> **📝 このドキュメントについて**  
> {Feature Name}のUIコンポーネント仕様書です。個別コンポーネントの詳細設計を定義しています。