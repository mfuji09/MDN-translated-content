---
title: "ContentVisibilityAutoStateChangeEvent: skipped プロパティ"
short-title: skipped
slug: Web/API/ContentVisibilityAutoStateChangeEvent/skipped
l10n:
  sourceCommit: 1c4eb0bfb5f72a26fcc21a83fac91aa3e66c2fb8
---

{{APIRef("CSS Containment")}}

`skipped` は {{ domxref("ContentVisibilityAutoStateChangeEvent") }} インターフェイスの読み取り専用プロパティで、ユーザーエージェントが[要素のコンテンツをスキップする](/ja/docs/Web/CSS/CSS_containment#skips_its_contents)場合は `true` を返し、そうでない場合は `false` を返します。

## 値

論理値です。ユーザーエージェントが要素のコンテンツをスキップした場合は `true` を返し、そうでない場合は `false` を返します。

## 例

```js
const canvasElem = document.querySelector("canvas");

canvasElem.addEventListener("contentvisibilityautostatechange", stateChanged);
canvasElem.style.contentVisibility = "auto";

function stateChanged(event) {
  if (event.skipped) {
    stopCanvasUpdates(canvasElem);
  } else {
    startCanvasUpdates(canvasElem);
  }
}

// キャンバスの更新を始める必要があるときに呼び出されます。
function startCanvasUpdates(canvas) {
  // …
}

// キャンバスの更新を停止する必要がある場合に呼び出されます。
function stopCanvasUpdates(canvas) {
  // …
}
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{domxref("element/contentvisibilityautostatechange_event", "contentvisibilityautostatechange")}} イベント
- [CSS 封じ込め](/ja/docs/Web/CSS/CSS_containment)
- {{cssxref("content-visibility")}} プロパティ
- {{cssxref("contain")}} プロパティ
