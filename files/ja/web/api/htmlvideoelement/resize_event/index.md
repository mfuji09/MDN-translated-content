---
title: "HTMLVideoElement: resize イベント"
short-title: resize
slug: Web/API/HTMLVideoElement/resize_event
l10n:
  sourceCommit: 73b2b6ee411ac094b9fc57dafac6f9c232fc20d9
---

{{APIRef("HTML DOM")}}

**`resize`** は {{domxref("HTMLVideoElement")}} インターフェイスのイベントで、{{domxref("HTMLVideoElement.videoWidth", "videoWidth")}} および {{domxref("HTMLVideoElement.videoHeight", "videoHeight")}} プロパティのうち、どちらか一方または両方が更新された直後に発行されます。

このイベントはキャンセル不可ですが、バブリングすることがあります。

## 構文

このイベント名を {{domxref("EventTarget.addEventListener", "addEventListener()")}} などのメソッドで使用するか、イベントハンドラープロパティを設定するかしてください。

```js
addEventListener("resize", (event) => {});

onresize = (event) => {};
```

## イベント型

一般的な {{domxref("Event")}} です。

## 例

```html
<video id="media" src="https://example.com/video.mp4"></video>
```

```js
const el = document.getElementById("media");
el.addEventListener("resize", () => {
  console.log("video 要素の大きさが変わりました。");
});
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{domxref("HTMLVideoElement.videoHeight")}}
- {{domxref("HTMLVideoElement.videoWidth")}}
