---
title: 視覚的ビューポート API
slug: Web/API/Visual_Viewport_API
l10n:
  sourceCommit: 4b5b3e16c8260a429db07dd54420ae40794b96c2
---

{{DefaultAPISidebar("Visual Viewport")}}

**視覚的ビューポート API** (Visual Viewport API) は、ウィンドウの{{Glossary("Visual Viewport", "視覚的ビューポート")}}のプロパティを問い合わせたり変更したりするための明確な仕組みを提供します。視覚的ビューポートとは、画面の内側にあるキーボード、ピンチズーム領域の外側、またはページの寸法に合わせて変倍しない画面上のその他の構成要素を除いた視覚的な部分のことです。

## 概念と使用方法

モバイルウェブには、レイアウトビューポートと視覚的ビューポートという 2 つのビューポートがあります。レイアウトビューポートはページ上のすべての要素をカバーし、視覚的ビューポートは画面に実際に表示される部分です。ユーザーがページ上でピンチズームを行うと、視覚的ビューポートは縮小しますが、レイアウトビューポートは変化しません。 画面上に表示されるキーボード (OSK) などのユーザーインターフェイス機能は、レイアウトビューポートに影響を与えることなく、視覚的ビューポートを縮小することがあります。

ウェブページの可視部分に関わらず、ウェブページの要素を画面上に表示する必要がある場合、何が起こるでしょうか？例えば、端末のピンチズームレベルに関わらず、一連の画像コントロールを常に画面上に表示する必要がある場合、どうなるでしょうか？現在のブラウザーでは、この処理方法に違いがあります。視覚的ビューポートを使用することで、ウェブ開発者は画面に表示されているものに対して要素を相対的に位置指定することで、この問題を解決することができます。

ウィンドウの視覚的ビューポートにアクセスするには、 {{domxref("VisualViewport")}} オブジェクトを {{domxref("Window.visualViewport")}} プロパティから取得します。このオブジェクトには、ビューポートを記述するプロパティのセットが含まれています。また、このオブジェクトには、{{domxref("VisualViewport/resize_event", "resize")}}、{{domxref("VisualViewport/scroll_event", "scroll")}}、{{domxref("VisualViewport/scrollend_event", "scrollend")}} という 3 つのイベントも追加されており、それぞれ視覚的ビューポートがリサイズされたとき、スクロールしたとき、スクロール動作がが完了したときにそれぞれ発行されます。

最初の2つのイベントでは、通常はレイアウトビューポートに固定されている要素を、スクロールやズームに合わせて視覚的ビューポートに対して相対的に位置指定することができます。 `scrollend` イベントでは、スクロールアクションが完了したときに要素を更新することができます。例えば、これらのイベントを使用して、ピンチズームやスクロールに合わせて要素を視覚的ビューポートに固定し、スクロールが終了したときに更新することができます。

## インターフェイス

- {{DOMxRef("VisualViewport")}}
  - : 指定されたウィンドウの視覚的ビューポートを表します。ウィンドウの `VisualViewport` オブジェクトは、ビューポートの位置とサイズに関する情報を提供し、{{domxref("VisualViewport.resize_event", "resize")}}、{{domxref("VisualViewport.scroll_event", "scroll")}}、{{domxref("VisualViewport.scrollend_event", "scrollend")}} の各イベントを受信します。

### 他のインターフェイスへの拡張

- {{domxref("Window.visualViewport")}} {{ReadOnlyInline}}
  - : ウィンドウの VisualViewport オブジェクトへの読み取り専用の参照。このプロパティが存在しない場合は、この API に対応していません。

## 例

[資格ビューポート API](https://mdn.github.io/dom-examples/visual-viewport-api/) の例では、 3 種類ののイベントを含むさまざまな視覚的ビューポート機能がどのように動作するのかの基本的なデモンストレーションをご覧いただけます。対応しているデスクトップおよびモバイルブラウザーで読み込み、ページをスクロールしたりピンチズームしたりしてみてください。 `resize` と `scroll` の際には、情報ボックスは視覚的ビューポートに対して同じ位置を維持するように再配置され、表示されるビューポートとスクロールの情報は更新されます。また、 `resize` と `scroll` の際にボックスの色を変更して、何かが現れたことを示し、 `scrollend` の際に元の色に戻します。

デスクトップブラウザーでは、ウィンドウがスクロールされると {{domxref("Window.scrollX")}} および {{domxref("Window.scrollY")}} の値が更新されますが、視覚的ビューポートの位置は変わりません。一方、モバイルブラウザーでは、通常、{{domxref("VisualViewport.offsetLeft")}} および {{domxref("VisualViewport.offsetTop")}} の値が更新されます。通常、ウィンドウの位置ではなく、視覚的ビューポートが変更されます。

例の HTML は次のようになります。情報ボックスは、 {{htmlelement("div")}} の `id` が `output` であるもので表現されます。

```html
<p id="instructions">
  スクロールしたりピンチズームしたりして、報告された値がどのように変化するかを試してみてください。
</p>
<div id="output">
  <p id="visual-info"></p>
  <hr />
  <p id="window-info"></p>
</div>
```

簡潔にするため、この例の CSS については説明しません。このデモでは重要ではありません。上記リンクの例で調べると確認できます。

JavaScript で、ページがズームやスクロールされた際に更新する情報ボックス、およびその情報ボックス内に含まれる 2 つの段落への参照をまず取得します。最初の段落には、報告された {{domxref("VisualViewport.offsetLeft")}} および {{domxref("VisualViewport.offsetTop")}} の値が入り、 2 つ目の段落には、報告された {{domxref("Window.scrollX")}} および {{domxref("Window.scrollY")}} の値が入ります。

```js
const output = document.getElementById("output");
const visualInfo = document.getElementById("visual-info");
const windowInfo = document.getElementById("window-info");
```

次に、イベントが発行された際に実行する 2 つのキーとなる関数を定義します。

- `scrollUpdater()` は、`resize` と `scroll` で発行されます。この関数は、{{domxref("VisualViewport.offsetTop")}} および {{domxref("VisualViewport.offsetLeft")}} プロパティを照会し、その値を使用して関連する{{glossary("Inset properties", "インセットプロパティ")}}の値を更新することで、視覚的ビューポートに対する情報ボックスの位置指定を更新します。また、情報ボックスの背景色を変更して何らかの動作中であることを示し、 `updateText()` 関数を実行してボックスに表示される値を更新します。
- `scrollEndUpdater()` 関数は `scrollend` で発行されます。これにより、情報ボックスが元の色に戻され、`updateText()` 関数が実行されて、 `scrollend` で最新の値が確実に表示されるようになります。

```js
const scrollUpdater = () => {
  output.style.top = `${visualViewport.offsetTop + 10}px`;
  output.style.left = `${visualViewport.offsetLeft + 10}px`;
  output.style.background = "yellow";
  updateText();
};

const scrollendUpdater = () => {
  output.style.background = "lime";
  updateText();
};
```

`updateText()` 関数は、最初の段落の {{domxref("HTMLElement.innerText")}} を設定して、現在の `VisualViewport.offsetLeft` と `VisualViewport.offsetTop` の値を表示させ、 2 つ目の段落の `HTMLElement.innerText` を設定して、現在の `Window.scrollX` と `Window.scrollY` の値を表示させるといった具合に動作します。 `updateText()` を定義した後、すぐにそれを呼び出すことで、ページ読み込み時に情報ボックスが正しく表示されるようにします。

```js
function updateText() {
  visualInfo.innerText = `視覚的ビューポートの左端: ${visualViewport.offsetLeft.toFixed(2)}
    上端: ${visualViewport.offsetTop.toFixed(2)}`;
  windowInfo.innerText = `Window scrollX: ${window.scrollX.toFixed(2)}
    scrollY: ${window.scrollY.toFixed(2)}`;
}

updateText();
```

> [!NOTE]
> 一部のブラウザーでは小数点以下の値が非常に多く表示される可能性があるため、 {{jsxref("Number.toFixed()")}} メソッドを使用してすべての値を小数点以下 2 桁に切り捨てます。

これで、モバイルとデスクトップの両方で適切なタイミングで主要な関数を実行するために、視覚的ビューポートと {{domxref("Window")}} オブジェクトの両方にイベントハンドラープロパティを設定しました。

- デスクトップブラウザーでページをスクロールする時など、一般的なウィンドウのスクロール操作で情報ボックスの位置やコンテンツが更新されるように、`window` にハンドラーを設定しました。
- モバイルブラウザーでページをスクロールしたりピンチズームしたりする際に、情報ボックスの位置やコンテンツが視覚的ビューポートのスクロールやズーム操作で更新されるように、`visualViewport` にハンドラーを設定しました。

```js
visualViewport.onresize = scrollUpdater;
visualViewport.onscroll = scrollUpdater;
visualViewport.onscrollend = scrollendUpdater;
window.onresize = scrollUpdater;
window.onscroll = scrollUpdater;
window.onscrollend = scrollendUpdater;
```

`scrollUpdater()` は `resize` と `scroll` で発行され、`scrollEndUpdater()` は `scrollend` で発行されます。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}
