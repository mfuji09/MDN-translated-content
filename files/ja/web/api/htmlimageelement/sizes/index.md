---
title: HTMLImageElement.sizes
slug: Web/API/HTMLImageElement/sizes
---

{{APIRef("HTML DOM")}}

{{domxref("HTMLImageElement")}} の **`sizes`** プロパティによって、メディア条件のリストごとに、画像のレイアウト幅を指定することができます。これにより、様々なメディア条件に合わせて文書の状態が変化したときに、異なる画像（方向やアスペクト比の異なる画像も含む）を自動的に選択する機能が提供されます。

それぞれの条件は、[メディアクエリー](/ja/docs/Web/CSS/Media_Queries)で使われているのと同じ条件指定の形式を使用します。

## 値

カンマで区切られたソースサイズ記述子のリストと、オプションで代替サイズを含む文字列。それぞれの**ソースサイズ記述子**は、メディア条件、 1 つ以上のホワイトスペース文字、そしてメディア条件が `true` と評価されたときに画像に使用する**ソースサイズ値**で構成されます。

#### メディア条件

それぞれのソースサイズ記述子は、メディアクエリー規格で定義されるメディア条件から構成される。ソースサイズ記述子は、ページのレイアウト中に画像に使用する幅を指定するために使用されるので、メディア条件は通常、幅の情報のみに基づきます（必ずしもそうとは限りません）。メディア条件の構築方法の詳細は[構文](/ja/docs/Web/CSS/Media_Queries/Using_media_queries#構文)を参照してください。

#### ソースサイズ値

ソースサイズの値は [CSS の長さ](/ja/docs/Web/CSS/length)です。フォントと相対的な単位 (`em` や `ex` など)、絶対的な単位 (`px` や `cm` など)、または `vw` という単位を使って指定することができ、ビューポート幅に対する割合（`1vw` はビューポート幅の 1%）で指定することができます。

> **メモ:** ソースサイズ値は、コンテナーサイズに対するパーセント値として指定してはいけません。つまり、`50%` や `100%` といった長さの指定は、指定した値が何に対するパーセント値であるかが不明確になるため、許されません。

## 例

この例では、ブログ風のレイアウトを作成し、テキストと画像を表示します。画像は、ウィンドウの幅に応じて 3 つのサイズポイントが指定されています。画像も 3 種類用意し、それぞれの幅を指定しています。ブラウザーはこれらの情報をすべて受け取り、指定された値に最も合う画像と幅を選択します。

画像がどのように使われるかは、ブラウザーやユーザーのディスプレイの画素密度に依存する場合があります。

この例の下にあるボタンで、実際に `sizes` プロパティを少し変更し、画像の 3 つの幅のうち最大のものを 40em と 50em の間で切り替えています。

### HTML

```html
<article>
  <h1>An amazing headline</h1>
  <div class="test"></div>
  <p>This is even more amazing content text. It's really spectacular.
     And fascinating. Oh, it's also clever and witty. Award-winning
     stuff, I'm sure.</p>
  <img src="/files/16870/new-york-skyline-wide.jpg"
       srcset="/files/16870/new-york-skyline-wide.jpg 3724w,
               /files/16869/new-york-skyline-4by3.jpg 1961w,
               /files/16871/new-york-skyline-tall.jpg 1060w"
       sizes="((min-width: 50em) and (max-width: 60em)) 50em,
              ((min-width: 30em) and (max-width: 50em)) 30em,
              (max-width: 30em) 20em">
  <p>Then there's even more amazing stuff to say down here. Can you
     believe it? I sure can't.</p>

  <button id="break40">Last Width: 40em</button>
  <button id="break50">Last Width: 50em</button>
</article>
```

### CSS

```css
article {
  margin: 1em;
  max-width: 60em;
  min-width: 20em;
  height: 100vh;
  border: 4em solid #880E4F;
  border-radius: 7em;
  padding: 1.5em;
  font: 16px "Open Sans", Verdana, Arial, Helvetica, sans-serif;
}

article img {
  display: block;
  max-width: 100%;
  border: 1px solid #888;
  box-shadow: 0 0.5em 0.3em #888;
  margin-bottom: 1.25em;
}
```

### JavaScript

JavaScript のコードでは、　3　つ目の幅のオプションを 40em と 50em の間で切り替えることができる　2　つのボタンを処理しています。これは {{domxref("Element.click_event", "click")}} イベントを処理することで、 JavaScript 文字列オブジェクトメソッド {{jsxref("String.replace", "replace()")}}を使って `sizes` 文字列の該当部分を置換して実現しています。

```js
let image = document.querySelector("article img");
let break40 = document.getElementById("break40");
let break50 = document.getElementById("break50");

break40.addEventListener("click",
    event => image.sizes = image.sizes.replace(/50em,/, "40em,"));

break50.addEventListener("click",
    event => image.sizes = image.sizes.replace(/40em,/, "50em,"));
```

### 結果

{{EmbedLiveSample("Example", 900, 850)}}

結果を{{LiveSampleLink('Example', '独自のウィンドウで見る')}}こともできます。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [Media queries](/ja/docs/Web/CSS/Media_Queries)
- [Using media queries](/ja/docs/Web/CSS/Media_Queries/Using_media_queries)
- [Images in HTML](/ja/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML)
- [Responsive images](/ja/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)
