---
title: initial-letter
slug: Web/CSS/initial-letter
l10n:
  sourceCommit: 33cd63a518c57caded1b43ff9fff071230a2397a
---

{{CSSRef}}

`initial-letter` は [CSS](/ja/docs/Web/CSS) のプロパティで、落ち文字、上げ文字、沈み文字の最初の文字のサイズとシンク（位置）を設定します。このプロパティは、 {{cssxref("::first-letter")}} 擬似要素とブロックコンテナーの最初のインラインレベルの子要素に適用されます。

## 構文

```css
/* キーワード値 */
initial-letter: normal;

/* 1 つの値 */
initial-letter: 3; /* 3 行の高さで、ベースラインは 3 行目 */
initial-letter: 1.5; /* 1.5 行の高さで、ベースラインは 2 行目 */

/* 2 つの値 */
initial-letter: 3 2; /* 3 行の高さで、ベースラインは 2 行目（1 行上がる） */
initial-letter: 3 1; /* 3 行の高さで、ベースラインは変更なし（2 行上がる） */

/* グローバル値 */
initial-letter: inherit;
initial-letter: initial;
initial-letter: revert;
initial-letter: revert-layer;
initial-letter: unset;
```

### 値

キーワード値の `normal`、または `<number>` と、その後に任意で `<integer>` が付きます。

- `normal`
  - : 頭文字に特別な効果を付与しません。テキストは普通通りに表示されます。
- `<number>`
  - : 頭文字のサイズを、何行を占めるかで指定します。負の値は使用できません。
- `<integer>`
  - : サイズが与えられたときに、頭文字が何行目に配置されるかを定義します。0 以上の値でなければなりません。省略された場合は、サイズの値を複製し、最も近い正の整数に切り捨てられます。

## 公式定義

{{cssinfo}}

## 形式文法

{{csssyntax}}

## 例

### 先頭文字のサイズの設定

#### HTML

```html-nolint live-sample___setting_initial_letter_size
<p class="normal">Initial letter は通常</p>
<p class="onefive">Initial letter は 1.5 行を占める</p>
<p class="three">Initial letter は 3 行を占める</p>
```

#### CSS

```css live-sample___setting_initial_letter_size
.normal::first-letter {
  -webkit-initial-letter: normal;
  initial-letter: normal;
}

.onefive::first-letter {
  -webkit-initial-letter: 1.5;
  initial-letter: 1.5;
}

.three::first-letter {
  -webkit-initial-letter: 3;
  initial-letter: 3;
}

p {
  outline: 1px dashed red;
}
```

#### 結果

{{EmbedLiveSample('Setting_initial_letter_size', 250, 180)}}

### シンク値の設定

この例では、すべての大文字の文字サイズは同じですが、シンク（位置）の値は異なります。

#### HTML

```html-nolint live-sample___setting_the_sink_value
<p class="four">Initial letter: シンク値 = 4</p>
<p class="same">Initial letter: シンク値は未宣言（サイズと同じ）</p>
<p class="two">Initial letter: シンク値 = 2</p>
<p class="one">Initial letter: シンク値 = 1</p>
```

#### CSS

```css live-sample___setting_the_sink_value
.four::first-letter {
  -webkit-initial-letter: 3 4;
  initial-letter: 3 4;
}

.same::first-letter {
  -webkit-initial-letter: 3;
  initial-letter: 3;
}

.two::first-letter {
  -webkit-initial-letter: 3 2;
  initial-letter: 3 2;
}

.one::first-letter {
  -webkit-initial-letter: 3 1;
  initial-letter: 3 1;
}

p {
  outline: 1px dashed red;
}
```

#### 結果

{{EmbedLiveSample('Setting_the_sink_value', 250, 240)}}

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{cssxref("::first-letter")}}
- {{cssxref(":first-child")}}
- [Drop caps in CSS](https://www.oddbird.net/2017/01/03/initial-letter/) (Oddbird, 2017)
