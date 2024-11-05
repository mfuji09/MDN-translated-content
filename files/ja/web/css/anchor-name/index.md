---
title: anchor-name
slug: Web/CSS/anchor-name
page-type: css-property
l10n:
  sourceCommit: 839c5e88a078deead1bcf1b2837d05499cb859b1
---

{{CSSRef}}{{seecompattable}}

[CSS](/ja/docs/Web/CSS) の **`anchor-name`** プロパティは、 1 つまたは複数の識別**アンカー名**を指定することで、要素を**アンカー要素**として定義できるようにします。それぞれの名前は、位置指定された要素の {{cssxref("position-anchor")}} プロパティの値として設定し、アンカーと関連付けることができます。

## 構文

```css
/* 単一値 */
anchor-name: none;
anchor-name: --name;

/* 複数値 */
anchor-name: --name, --another-name;

/* グローバル値 */
anchor-name: inherit;
anchor-name: initial;
anchor-name: revert;
anchor-name: revert-layer;
anchor-name: unset;
```

### 値

- `none`

  - : 既定値です。要素に `anchor-name: none` を設定すると、その要素がアンカー要素として定義されていないということになります。 要素が以前にアンカーとして定義され、位置指定された要素と関連付けられていた場合、`anchor-name: none` を設定すると、両者の関連付けが解除されます。

- {{cssxref("dashed-ident")}}
  - : カンマで区切られた任意のカスタム識別子を1つ以上定義し、アンカーの名前または名前付きを定義します。この識別子は、{{cssxref("position-anchor")}}プロパティで参照することができます。

## 解説

要素をアンカー要素に対して相対的に位置指定するには、位置指定された要素に 3 つの機能、すなわち関連付け、位置、場所が必要となります。 `anchor-name` および {{cssxref("position-anchor")}} プロパティは、関連付けを提供します。

アンカー要素は、 `anchor-name` プロパティを介して設定された 1 つまたは複数の `<dashed-ident>` のアンカー名を受け入れます。 {{cssxref("position")}} が `absolute` または `fixed` の要素において、これらの名前の 1 つが `position-anchor` プロパティの値として設定されると、 2 つの要素が関連付けられます。 関連付けられた要素の位置がアンカーに対して相対的に指定されることで、 2 つの要素が関連付けられ、関連付けられた要素が「アンカー位置指定」要素となります。

複数のアンカー要素に同じアンカー名が設定されており、その名前が位置指定要素の `position-anchor` プロパティ値によって参照されている場合、その位置指定要素は、そのアンカー名を持つアンカー要素のうち、ソース順で最後に設定されたものに関連付けられます。

アンカーを位置指定すると、アンカー位置指定要素の[包含ブロック](/ja/docs/Web/CSS/Containing_block)を変更し、その `position` を、最も近い位置指定された祖先要素ではなく、アンカーに対して相対的なものにします。

アンカー要素に相対で指定された場所に配置された要素を固定するには、アンカーの位置指定機能が必要です。例えば、 {{cssxref("anchor()")}} 関数（{{glossary("inset properties", "インセットプロパティ")}}の値内に設定する）や {{cssxref("position-area")}} プロパティなどです。

アンカーが非表示（{{cssxref("display", "display: none")}} や {{cssxref("visibility", "visibility: hidden")}}）の場合、またはアンカーが[スキップコンテンツの一部](/ja/docs/Web/CSS/CSS_containment/Using_CSS_containment#skips_its_contents)で {{cssxref("content-visibility", "content-visibility: hidden")}} が設定されている場合、位置指定要素をアンカー要素と関連付けることはできません。

`anchor-name` プロパティは、基本ボックスを生成するすべての要素で対応しています。つまり、 {{cssxref("::before")}} や {{cssxref("::after")}} などを使用して生成された生成コンテンツ、 [`range` 入力](/ja/docs/Web/HTML/Element/input/range)のつまみ ({{cssxref("::-webkit-slider-thumb")}}) などの UI 機能の[擬似要素](/ja/docs/Web/CSS/Pseudo-elements)も、アンカー要素として使用することができます。擬似要素は、特に指定がない限り、擬似要素の元となる要素と同じ要素に暗黙的にアンカー付けされます。

アンカー機能および使用方法の詳細については、 [CSS アンカー位置指定](/ja/docs/Web/CSS/CSS_anchor_positioning)モジュールのランディングページおよび [CSS アンカー位置指定の使用](/ja/docs/Web/CSS/CSS_anchor_positioning/Using)ガイドを参照してください。

## 公式定義

{{cssinfo}}

## 形式文法

{{csssyntax}}

## 例

### 基本的な例

この例では、位置指定された要素がアンカーに結び付けられ、要素がアンカーの右側に位置指定されます。

#### HTML

2 つの {{htmlelement("div")}} 要素を指定します。クラス名が `anchor` であるアンカー要素と、クラス名が `infobox` である位置指定要素です。

また、 2 つの `<div>` 要素の周りには、 {{htmlelement("body")}} がスクロールするように高さを出すための詰め物テキストが入っています。

```html
<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
  incididunt ut labore et dolore magna aliqua. Dui nunc mattis enim ut tellus
  elementum sagittis vitae et.
</p>

<div class="anchor">⚓︎</div>

<div class="infobox">
  <p>これが情報ボックスです。</p>
</div>

<p>
  Nisi quis eleifend quam adipiscing vitae proin sagittis nisl rhoncus. In arcu
  cursus euismod quis viverra nibh cras pulvinar. Vulputate ut pharetra sit amet
  aliquam.
</p>

<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique. Porta lorem mollis aliquam ut porttitor. Turpis cursus in hac
  habitasse platea dictumst quisque. Dolor sit amet consectetur adipiscing elit.
  Ornare lectus sit amet est placerat. Nulla aliquet porttitor lacus luctus
  accumsan.
</p>
```

#### CSS

まず、 `anchor` の `<div>` を、 `anchor-name` プロパティでアンカー名を設定することでアンカー要素として宣言します。

```css hidden
body {
  width: 50%;
  margin: 0 auto;
}

.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}
```

```css
.anchor {
  anchor-name: --myAnchor;
}
```

2 つ目の `<div>` は、アンカー要素に関連付けられています。アンカーの名前を、位置指定された要素の {{cssxref("position-anchor")}} プロパティの値として設定することで、関連付けられています。次に、位置指定要素に以下の項目を設定します。

- {{cssxref("position")}} プロパティを `fixed` に変更し、アンカー位置指定要素に変換することで、ページ上のアンカーの位置に対して相対的に位置指定できるようになります。
- {{cssxref("left")}} および {{cssxref("top")}} プロパティを {{cssxref("anchor()")}} 関数に設定し、それぞれ `right` および `top` の値を指定します。これにより、情報ボックスの左端がアンカーの右端に揃えられ、上端がアンカーの上端に相対的に位置指定されます。
- {{cssxref("margin-left")}} を `10px` に設定し、アンカー位置指定要素とアンカーの間に空間を作成します。

```css hidden
.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #ddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

```css
.infobox {
  position-anchor: --myAnchor;
  position: fixed;
  left: anchor(right);
  top: anchor(top);
  margin-left: 10px;
}
```

#### 結果

ページをスクロールして、アンカーと情報ボックスの相対的な位置関係を確認してください。アンカーが上方向にスクロールすると、位置指定された要素も一緒に移動します。

{{ EmbedLiveSample("Basic usage", "100%", "225") }}

### 複数の位置指定要素

この例では、複数の位置指定要素を 1 つのアンカーに関連付けられる方法を示します。

#### HTML

HTML は前回と同じですが、今回は、それらを識別するための異なる [`id`](/ja/docs/Web/HTML/Global_attributes/id) を持つ複数の位置指定要素 `<div>` があるという点が異なります。

```html
<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
  incididunt ut labore et dolore magna aliqua. Dui nunc mattis enim ut tellus
  elementum sagittis vitae et.
</p>

<div class="anchor">⚓︎</div>

<div class="infobox" id="infobox1">
  <p>これが情報ボックスです。</p>
</div>

<div class="infobox" id="infobox2">
  <p>これがもう一つの情報ボックスです。</p>
</div>

<p>
  Nisi quis eleifend quam adipiscing vitae proin sagittis nisl rhoncus. In arcu
  cursus euismod quis viverra nibh cras pulvinar. Vulputate ut pharetra sit amet
  aliquam.
</p>

<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique. Porta lorem mollis aliquam ut porttitor. Turpis cursus in hac
  habitasse platea dictumst quisque. Dolor sit amet consectetur adipiscing elit.
  Ornare lectus sit amet est placerat. Nulla aliquet porttitor lacus luctus
  accumsan.
</p>
```

#### CSS

前回と同様に、 `anchor` の `<div>` に対して、 `anchor-name` プロパティでアンカー名を設定することで、アンカー要素として宣言します。

```css hidden
body {
  width: 50%;
  margin: 0 auto;
}

.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}
```

```css
.anchor {
  anchor-name: --myAnchor;
}
```

2 つの配置された要素は、そのアンカー名を位置指定要素の {{cssxref("position-anchor")}} プロパティ値として設定することで、アンカー要素に関連付けられています。どちらも `fixed` で位置指定され、**アンカー位置指定要素**となります。位置指定された要素は、上記のインセットプロパティの組み合わせと、 {{cssxref("align-self")}} / {{cssxref("justify-self")}} プロパティの値に `anchor-center` を使用することで、アンカーに対して異なる位置に配置されます。これにより、インラインまたはブロックの方向で、情報ボックスがアンカーの中央にそれぞれ中央揃えされます。

```css hidden
.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #ddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

```css
.infobox {
  position-anchor: --myAnchor;
  position: fixed;
}

#infobox1 {
  left: anchor(right);
  align-self: anchor-center;
  margin-left: 10px;
}

#infobox2 {
  bottom: anchor(top);
  justify-self: anchor-center;
  margin-bottom: 15px;
}
```

#### 結果

ページをスクロールして、どちらの情報ボックスもアンカーに結び付けられていることを確認してください。

{{ EmbedLiveSample("Multiple positioned elements", "100%", "225") }}

### 複数のアンカー名

この例では、アンカー要素が複数のアンカー名を持つことができることを説明しています。

#### HTML

HTML は、前回の例と同じです。

```html hidden
<p>
  Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
  incididunt ut labore et dolore magna aliqua. Dui nunc mattis enim ut tellus
  elementum sagittis vitae et.
</p>

<div class="anchor">⚓︎</div>

<div class="infobox" id="infobox1">
  <p>これが情報ボックスです。</p>
</div>

<div class="infobox" id="infobox2">
  <p>これがもう一つの情報ボックスです。</p>
</div>

<p>
  Nisi quis eleifend quam adipiscing vitae proin sagittis nisl rhoncus. In arcu
  cursus euismod quis viverra nibh cras pulvinar. Vulputate ut pharetra sit amet
  aliquam.
</p>

<p>
  Malesuada nunc vel risus commodo viverra maecenas accumsan lacus. Vel elit
  scelerisque mauris pellentesque pulvinar pellentesque habitant morbi
  tristique. Porta lorem mollis aliquam ut porttitor. Turpis cursus in hac
  habitasse platea dictumst quisque. Dolor sit amet consectetur adipiscing elit.
  Ornare lectus sit amet est placerat. Nulla aliquet porttitor lacus luctus
  accumsan.
</p>
```

#### CSS

CSS は前回と同じですが、ターゲットの `anchor-name` プロパティ値にカンマで区切った 2 つの名前を記載しており、それぞれの位置指定要素で `position-anchor` に様々な値を設定してある点を除いては、前回と同じです。

```css hidden
body {
  width: 50%;
  margin: 0 auto;
}

.anchor {
  font-size: 1.8rem;
  color: white;
  text-shadow: 1px 1px 1px black;
  background-color: hsl(240 100% 75%);
  width: fit-content;
  border-radius: 10px;
  border: 1px solid black;
  padding: 3px;
}

.infobox {
  color: darkblue;
  background-color: azure;
  border: 1px solid #ddd;
  padding: 10px;
  border-radius: 10px;
  font-size: 1rem;
}
```

```css
.anchor {
  anchor-name: --anchor1, --anchor2;
}

.infobox {
  position: fixed;
}

#infobox1 {
  position-anchor: --anchor1;
  left: anchor(right);
  align-self: anchor-center;
  margin-left: 10px;
}

#infobox2 {
  position-anchor: --anchor2;
  bottom: anchor(top);
  justify-self: anchor-center;
  margin-bottom: 15px;
}
```

#### 結果

ページをスクロールして、どちらの情報ボックスもアンカーに結び付けられていることを確認してください。

{{ EmbedLiveSample("Multiple anchor names", "100%", "225") }}

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{cssxref("position-anchor")}}
- HTML の [`anchor`](/ja/docs/Web/HTML/Global_attributes/anchor) 属性
- [CSS アンカー位置指定](/ja/docs/Web/CSS/CSS_anchor_positioning)モジュール
- [CSS アンカー位置指定の使用](/ja/docs/Web/CSS/CSS_anchor_positioning/Using)ガイド
