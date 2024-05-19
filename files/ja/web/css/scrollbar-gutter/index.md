---
title: scrollbar-gutter
slug: Web/CSS/scrollbar-gutter
l10n:
  sourceCommit: c2a472faa513c29e43c014c76803fbb042c0a86b
---

{{CSSRef}}

**`scrollbar-gutter`** は [CSS](/ja/docs/Web/CSS) プロパティで、製作者がスクロールバーの空間を確保し、コンテンツの増加に伴うレイアウトの不要な変更を避けると同時に、スクロールが不要な場合は不要なビジュアルを避けることができます。

要素のスクロールバーガターは、境界線の内側の端とパディングの外側の端の間の空間で、ブラウザーはここにスクロールバーを表示することができます。スクロールバーが存在しない場合、ガターはパディングの延長として描画されます。

ブラウザーは、伝統的スクロールバーとオーバーレイスクロールバーのどちらを使用するかを決定します。

- 伝統的スクロールバーは、常にガターに配置され、存在する場合は空間を消費します。
- オーバーレイスクロールバーは、ガターではなくコンテンツの上に配置され、通常は部分的に透明です。

## 構文

```css
/* 初期値 */
scrollbar-gutter: auto;

/* "stable" キーワードと、オプションの修飾子 */
scrollbar-gutter: stable;
scrollbar-gutter: stable both-edges;

/* グローバル値 */
scrollbar-gutter: inherit;
scrollbar-gutter: initial;
scrollbar-gutter: revert;
scrollbar-gutter: revert-layer;
scrollbar-gutter: unset;
```

### 値

- `auto`
  - : 初期値です。伝統的スクロールバーは `overflow` が `scroll` の場合、または `overflow` が `auto` でボックスがオーバーフローしている場合にガターを作成します。オーバーレイスクロールバーは空間を消費しません。
- `stable`
  - : クラシックスクロールバーを使用している場合、 `overflow` が `auto`、`scroll`、`hidden` のいずれかに設定されていると、ボックスがオーバーフローしていなくてもガターが表示されます。オーバーレイスクロールバーを使用している場合、ガターは表示されません。
- `both-edges`
  - : ボックスのインライン軸の先頭または末尾の端の一方にガターが存在する場合、反対側のエッジにも空間が取られます。

## 公式定義

{{cssinfo}}

## 形式文法

{{csssyntax}}

## 例

下記の例は、`scrollbar-gutter` プロパティの異なる値が、1 つ以上の段落を格納したスクロール可能な `div` 要素 (`.container`) にどのような影響を与えるかを示しています。

> **メモ:** この例の画像では、ユーザーのシステム設定を伝統的スクロールバー（常に表示させる）に設定しています。

### 例 1

コンテンツが大きくなったり小さくなったりすることで、スクロールバーが現れたり消えたりするため、そのための空間が確保され、不要なレイアウト変更を防ぐことができます。

```css
.container {
  scrollbar-gutter: stable;
}
```

![テキストの段落をコンテナーの中に格納し、スクロールバーがある右側に空間を設けたコンテナー。](stable-no-scroll.png)

### 例 2

ボックスの両側に左右対称の空間を追加し、コンテンツが中央に配置されるようにします。

```css
.container {
  scrollbar-gutter: stable both-edges;
}
```

![コンテナーの中にテキストの段落を格納する div 要素、スクロールバーのある右側の空間と一致する左側の空の空間](stable-both-edges.png)

### 例 3

スクロールしない要素と、それに隣接するスクロールする要素のコンテンツを配置します。
この例では、2 つの div を横に並べて表示しています。左側のものはスクロールを保有していませんが、右側のものは保有しています。どちらも `scrollbar-gutter` が適用されており、スクロール可能なコンテンツがない左側の div の空間も確保されています。これはコンテンツの幅を一定に保つために使用する良いテクニックです。

```css
.container1 {
  overflow: hidden;
  scrollbar-gutter: stable;
}

.container2 {
  scrollbar-gutter: stable;
}
```

![テキストを格納する 2 つの隣接する div で、両方ともスクロールバーのための空間があります。](side-by-side.png)

### オーバーレイスクロールバー

参考までに、この画像は上と同じ div を表示していますが、ユーザーのシステム設定でスクロールバーをオーバーレイするように設定されています。ここでは、スクロールバーはユーザーがスクロールしているときと、コンテンツの上にあるときにのみ表示させるので、そのための空間は確保されず、`scrollbar-gutter`プロパティは効果がないことに注意してください。

![テキストを含む 1 つの div、スクロールバーの表示なし](for-ref-no-scroll.png)

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [CSS オーバーフロー](/ja/docs/Web/CSS/CSS_overflow)モジュール
- [CSS スクロールバースタイル設定](/ja/docs/Web/CSS/CSS_scrollbars_styling)モジュール
- {{CSSxRef("overflow")}}
- {{CSSxRef("scrollbar-width")}}
- {{CSSxRef("scrollbar-color")}}
