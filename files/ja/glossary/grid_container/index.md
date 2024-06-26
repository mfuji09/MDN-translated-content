---
title: Grid container (グリッドコンテナー)
slug: Glossary/Grid_Container
l10n:
  sourceCommit: 3c5185e55298c2ca14e4e63913a50bb81e3c5609
---

{{GlossarySidebar}}

要素に `grid` または `inline-grid` を使用すると、[CSS グリッドレイアウト](/ja/docs/Web/CSS/CSS_grid_layout)の**グリッドコンテナー**になります。そして直下の子要素はグリッドアイテムになります。

要素がグリッドコンテナーになると、**グリッド整形コンテキスト**を形成します。グリッドコンテナー直下の子要素は、{{cssxref("grid-template-columns")}} や {{cssxref("grid-template-rows")}}を使って明示的に定義されたグリッドや、明示的に定義されたグリッドの外側に置かれた時には暗黙的に形成されるグリッドに沿って、配置されます。

## 関連情報

### プロパティリファレンス

- {{cssxref("grid-template-columns")}}
- {{cssxref("grid-template-rows")}}
- {{cssxref("grid-auto-columns")}}
- {{cssxref("grid-auto-rows")}}
- {{cssxref("grid")}}
- {{cssxref("grid-template")}}

### 参考文献

- [グリッドレイアウトの基本概念](/ja/docs/Web/CSS/CSS_grid_layout/Basic_concepts_of_grid_layout)
