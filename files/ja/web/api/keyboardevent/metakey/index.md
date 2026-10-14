---
title: "KeyboardEvent: metaKey プロパティ"
short-title: metaKey
slug: Web/API/KeyboardEvent/metaKey
l10n:
  sourceCommit: 358daf81ac9cf3db999cc8af7aed81ef4ff0c3f6
---

{{APIRef("UI Events")}}

**`KeyboardEvent.metaKey`** は読み取り専用のプロパティで、 プロパティは、イベントが発生したときに <kbd>Meta</kbd> キーが押されていたか (`true`) あるいは押されていなかった (`false`) かを示す論理値を返します。オペレーティングシステムによっては、キーが検出されないように遮蔽されることがあります。

> [!NOTE]
> Macintosh のキーボードでは、これは <kbd>⌘ Command</kbd> キーです。

> [!NOTE]
> Firefox 118 以前では、<kbd>⊞ Windows</kbd> キーは "Meta" キーではなく "OS" キーとして処理されていました。<kbd>⊞ Windows</kbd> キーが押された際、`KeyboardEvent.metaKey` の値は `false` となっていました。

<kbd>Meta</kbd> キー自体が押されたり離されたりした際、このプロパティは、{{domxref("Element/keydown_event", "keydown")}} イベントでは `true` となり、{{domxref("Element/keyup_event", "keyup")}} イベントでは `false` となります。これは、どちらのイベントも状態の変化の後に発生するためです。

## 値

論理値です。

## 例

```html
<button>Click me with the meta key</button>

<p id="output"></p>
```

```js
document.querySelector("button").addEventListener("click", (e) => {
  document.querySelector("#output").textContent =
    `metaKey pressed? ${e.metaKey}`;
});
```

#### 結果

{{ EmbedLiveSample('Examples', 400, 90) }}

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{ domxref("KeyboardEvent") }}
