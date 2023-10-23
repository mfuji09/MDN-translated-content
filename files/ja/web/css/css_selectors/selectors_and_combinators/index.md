---
title: CSS セレクターと結合子
slug: Web/CSS/CSS_selectors/Selectors_and_combinators
l10n:
  sourceCommit: bb652aaf3e38f3c7fef970a62f813047dffac879
---

{{CSSRef("Selectors")}}

CSS セレクターは、選択した要素に一連の CSS ルールを適用するために、選択したい要素のパターンを定義するために使用します。結合子は、セレクター間の関係を定義します。様々なセレクターと結合子を使用することで、要素の型、属性、状態、他の要素との関係に基づいて、必要な要素を正確に選択し、スタイル設定することができます。

## セレクターの種類

セレクターと結合子は 80 以上あります。 CSS セレクターは、選択する要素の種類によって以下のカテゴリーに分類されます。

### 基本セレクター

[型セレクター](/ja/docs/Web/CSS/Type_selectors)は、指定されたノード名を持つ要素をすべて選択します。例えば `div` はすべての {{HTMLElement("div")}} 要素を選択し、 `input` はすべての {{HTMLElement("input")}} 要素に一致します。アスタリスク (`*`) で示される[全称セレクター](/ja/docs/Web/CSS/Universal_selectors)は、すべての要素を選択する特別な種類のセレクターです。

[クラスセレクター](/ja/docs/Web/CSS/Class_selectors)は、ピリオド (`.`) を接頭辞とするクラス名で指定された `class` 属性を持つ要素をすべて選択します。例えば、 `.index` は `class="index"` を持つすべての要素に照合します。 [ID セレクター](/ja/docs/Web/CSS/ID_selectors) は `id` 属性の値に基づいて要素を選択します。セレクターは `id` の接頭辞に「番号記号」 (U+0023, `#`) を付けたものです。例えば、 `#toc` は `id="toc"` を持つ要素に一致します。[`class`](/ja/docs/Web/HTML/Global_attributes/class) と [`id`](/ja/docs/Web/HTML/Global_attributes/id) はどちらもグローバル属性です。文書内の指定された `id` を持つ要素は 1 つだけであるべきですが、もし複数の要素がある場合、 ID セレクターはその `id` を持つすべての要素に一致します。

[複合セレクター](/ja/docs/Web/CSS/CSS_selectors/Selector_structure#複合セレクター)を作成するために、型または全称セレクターをクラスまたは id セレクターと結合する場合、型または全称セレクターはクラスまたは id の前になければなりません。

#### CSS

この例では、 4 つの[単純セレクター](/ja/docs/Web/CSS/CSS_selectors/Selector_structure#単純セレクター)と、 1 つの[複合セレクター](/ja/docs/Web/CSS/CSS_selectors/Selector_structure#複合セレクター)を、上記の 4 種類の基本セレクターを使用して宣言しています。

```css
* {
  font-style: italic;
}
p {
  color: red;
}
.myClass {
  text-decoration: underline;
}
#myId {
  font-family: monospace;
}
p.myClass#myId {
  font-size: 1.5rem;
}
```

#### HTML

```html
<p class="myClass" id="myId">すべてに一致します。</p>
<p>全称セレクターと型セレクターにだけ一致します。</p>
```

#### 結果

{{EmbedLiveSample("Basic selectors", "100%", 100)}}

## 結合子

CSS の結合子を使用すると、セレクターを組み合わせて、文書ノードツリー内の他の要素との関係に基づいて DOM ノードを選択することができます。このセレクターと結合子の組み合わせによって、[複雑セレクター](/ja/docs/Web/CSS/CSS_selectors/Selector_structure#複雑セレクター)が作成されます。

### 子孫結合子

[子孫結合子](/ja/docs/Web/CSS/Descendant_combinator)は 1 つ以上のスペースで示され、最初の要素の子孫であるノードを選択します。例えば、 `div span` は {{HTMLElement("div")}} 要素の中にあるすべての {{HTMLElement("span")}} 要素に一致します。

### 子結合子

[子結合子](/ja/docs/Web/CSS/Child_combinator)は子孫結合子よりもさらに詳細です。大なり文字 (`>`) で示される子結合子は、最初の要素の直接の子であるノードを選択します。前回の例と比較すると、 `div > span` は {{HTMLElement("div")}} 要素の直接の子である {{HTMLElement("span")}} 要素のみに一致します。

### 後続兄弟結合子

子孫セレクターに加えて、 CSS は兄弟姉妹に基づいて要素を選択することもできます。チルダ (`~`) で示される[後続兄弟結合子](/ja/docs/Web/CSS/Subsequent-sibling_combinator)は兄弟要素を選択します。 `A ~ B` が指定された場合、`A` の前に `B` があり、`A` と `B` が同じ親であれば、`B` に一致する要素がすべて選択されます。例えば、 `h2 ~ p` は、{{HTMLElement("Heading_Elements", "h2")}} の次の例に続くすべての {{HTMLElement("p")}} 要素に一致します。

### 次兄弟結合子

[次兄弟結合子](/ja/docs/Web/CSS/Next-sibling_combinator)はプラス記号 (`+`) で示され、後続兄弟結合子に似ています。ただし、`A + B` が指定された場合、`B` の直前に `A` があり、両者が同じ親を共有している場合にのみ `B` に一致します。前回の例を修正すると、 `h2 + p` は `<h2>` 要素の直後に続く単一の `<p>` 要素にのみ一致します。

### 列結合子

[列結合子](/ja/docs/Web/CSS/Column_combinator)は 2 つのパイプ文字 (`||`) で示され、対応している場合、列に属するノードを選択します。例えば、 `col || td` は {{HTMLElement("col")}} のスコープに属するすべての {{HTMLElement("td")}} 要素に照合します。

### 名前空間区切り文字

[名前空間区切り文字](/ja/docs/Web/CSS/Namespace_separator)は、一般的に {{CSSXref("@namespace")}} アットルールと組み合わせて使用するもう一つの結合子です。この結合子は単一のパイプ文字 (`|`) で示されます。これにより、[型セレクター](/ja/docs/Web/CSS/Type_selectors) と[全称セレクター](/ja/docs/Web/CSS/Universal_selectors)を特定の名前空間に限定することができます。例えば、`@namespace SVG url('http://www.w3.org/2000/svg');` のように名前空間を定義することで、 SVG 名前空間に入れ子になっている要素のみを対象とするセレクターを含めることができます。 `SVG|a` と宣言すれば、 SVG 内のリンクに一致し、文書内の他の要素には一致しません。名前空間は HTML 内の MathML や SVG、他にも XML ベースのコンテンツを対象とするのに有益なものです。

#### CSS

この例では、結合子と組み合わせた[単純セレクター](/ja/docs/Web/CSS/CSS_selectors/Selector_structure#単純セレクター)を使用して、 5 つの[相対セレクター](/ja/docs/Web/CSS/CSS_selectors/Selector_structure#相対セレクター)を宣言しています。

```css
h2 + p ~ p {
  font-style: italic;
}
h2 + p + p {
  color: red;
}
.myClass + p {
  text-decoration: underline;
}
#myId > .myClass {
  outline: 3px dashed red;
}
> p {
  font-size: 1.1rem;
}
```

#### HTML

```html
<h2 class="myClass" id="myId">
  一致するセレクターなし。<span class="myClass">この span には輪郭線があります</span>。 myClass であり、 #myId の子でもあるためです。
</h2>
<p>最初の段落には下線が引かれています。すべての段落は 1.1rem です。</p>
<p>
  2 つ目は赤です。この段落と以下の段落はイタリック体です。
</p>
<p>3 つ目は赤ではありません。イタリック体で 1.1rem です。</p>
<p class="myClass">
  H2 の兄弟であり、子ではありません。イタリック体で 1.1rem です。
</p>
```

#### 結果

{{EmbedLiveSample("Combinators", "100%", 300)}}

### CSS 入れ子で複雑セレクターを作成する方法

上記の複雑セレクタはー、単純セレクター、結合子、[CSS 入れ子](/ja/docs/Web/CSS/CSS_nesting)を使用して定義することもでき、 [`&` 入れ子セレクター](/ja/docs/Web/CSS/Nesting_selector)を使用することも、使用しないこともできます。

#### CSS

この例では、単純セレクターと結合子を使用して同じ 5 つの相対セレクターを複製しますが、今回は CSS 入れ子を使用します。

```css
h2 {
  & + p {
    & ~ p {
      font-style: italic;
    }
    & + p {
      color: red;
    }
  }
}
.myClass {
  & + p {
    text-decoration: underline;
  }
}
#myId {
  & > .myClass {
    outline: 3px dashed red;
  }
}
> p {
  font-size: 1.1rem;
}
```

#### HTML

```html
<h2 class="myClass" id="myId">
  一致するセレクターなし。<span class="myClass">この span には輪郭線があります</span>。 myClass であり、 #myId の子でもあるためです。
</h2>
<p>最初の段落には下線が引かれています。すべての段落は 1.1rem です。</p>
<p>
  2 つ目は赤です。この段落と以下の段落はイタリック体です。
</p>
<p>3 つ目は赤ではありません。イタリック体で 1.1rem です。</p>
<p class="myClass">
  H2 の兄弟であり、子ではありません。イタリック体で 1.1rem です。
</p>
```

#### 結果

{{EmbedLiveSample("creating_complex_selectors_with_css_nesting", "100%", 300)}}

## 属性セレクター

[属性セレクター](/ja/docs/Web/CSS/Attribute_selectors) は、セレクターの書き方によって、指定された属性を持つか、指定された属性と値が一致する要素をすべて選択します。
例えば、`[type]` は `type` 属性が（任意の値に）設定されているすべての要素に一致し、`[type="submit"]` は `<input type="submit">`と `<button type="submit">`、または `type="submit"` が設定されている要素に一致します。この属性と値の組は {{HTMLElement("input")}} と {{HTMLElement("button")}} 要素でしか対応していないとしてもです。照合は大文字と小文字を区別しません。

属性の大文字と小文字の区別は言語に依存します。一般に HTML では、属性が{{glossary("enumerated", "列挙型")}}の場合、値が列挙された値でなくても、属性が設定するには有効な値でなくても、セレクターの値は大文字と小文字を区別しません。`class`、`id`、`data-*` 属性のような列挙されない属性、または `role` や `aria-*` 属性のような非 HTML 属性では、値の照合は大文字と小文字を区別します; 照合は大文字と小文字を区別しない修飾子 (`i`) で区別することができます。

## 擬似クラスセレクター

[CSS セレクター](/ja/docs/Web/CSS/CSS_selectors)モジュールでは、 60 以上の[擬似クラス](/ja/docs/Web/CSS/Pseudo-classes)を定義しています。擬似クラスはコロン (`:`) を接頭辞とする[単純セレクター](#単純セレクター)で、文書ツリー内に格納されていない状態情報に基づいて要素を選択できるようにします。 {{CSSxRef("pseudo-classes", "擬似クラス")}}は、状態に基づいて要素をスタイル設定するために使用することができます。
例えば、 {{cssxref(":target")}} 単純セレクターは、フラグメント識別子のついた URL の要素を対象とし、 [`a:visited`](/ja/docs/Web/CSS/:visited) [複合セレクター](/ja/docs/Web/CSS/CSS_selectors/Selector_structure#複合セレクター)はユーザーが訪問したすべての {{HTMLElement("a")}} 要素に一致します。

擬似要素は、[要素表示状態](/ja/docs/Web/CSS/Pseudo-classes#要素表示状態擬似クラス)、[入力](/ja/docs/Web/CSS/Pseudo-classes#入力擬似クラス)、[言語](/ja/docs/Web/CSS/Pseudo-classes#言語擬似クラス)、[位置](/ja/docs/Web/CSS/Pseudo-classes#位置擬似クラス)、[リソース状態](/ja/docs/Web/CSS/Pseudo-classes#リソース状態擬似クラス)、[時間軸](/ja/docs/Web/CSS/Pseudo-classes#時間軸擬似クラス)、[ツリー構造](/ja/docs/Web/CSS/Pseudo-classes#ツリー構造擬似クラス)、[ユーザー操作](/ja/docs/Web/CSS/Pseudo-classes#ユーザー操作擬似クラス)、[関数](/ja/docs/Web/CSS/Pseudo-classes#関数擬似クラス)に分類することができます。

複数の擬似クラスを組み合わせて[複合セレクター](#複合セレクター)を作成することができます。擬似クラスを型セレクターや全称セレクターと複合セレクターに結合する場合、擬似クラスは型セレクターや全称セレクターを表示する場合は、それに続かなければなりません。

## 擬似要素セレクター

すべての CSS セレクターが [CSS セレクターモジュール](/ja/docs/Web/CSS)で定義されているわけではありません。 CSS 擬似要素のセレクターは [CSS 擬似要素](/ja/docs/Web/CSS/CSS_pseudo-elements)モジュールで定義されています。

CSS の[擬似要素](/ja/docs/Web/CSS/Pseudo-elements)は、接頭辞にコロンを 2 つ付け (`::`)、HTMLには含まれない要素を表します。例えば、単純セレクターである {{cssxref("::marker")}} はリスト項目の箇条書きを選択し、複合セレクター [`p::first-line`](/ja/docs/Web/CSS/::first-line) はすべての {{HTMLElement("p")}} 要素の最初の行に一致します。

## 仕様書

{{Specifications}}

これらの詳細については[擬似クラス](/ja/docs/Web/CSS/Pseudo-classes#仕様書)と[擬似要素](/ja/docs/Web/CSS/Pseudo-elements#仕様書)の仕様書表を参照してください。

## 関連情報

- [セレクターリスト](/ja/docs/Web/CSS/Selector_list)
- [CSS セレクター構造](/ja/docs/Web/CSS/CSS_selectors/Selector_structure)
- [詳細度](/ja/docs/Web/CSS/Specificity)
- [CSS 入れ子モジュール](/ja/docs/Web/CSS/CSS_nesting)
