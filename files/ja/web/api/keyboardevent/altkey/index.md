---
title: "KeyboardEvent: altKey プロパティ"
short-title: altKey
slug: Web/API/KeyboardEvent/altKey
l10n:
  sourceCommit: 358daf81ac9cf3db999cc8af7aed81ef4ff0c3f6
---

{{APIRef("UI Events")}}

**`KeyboardEvent.altKey`** は読み取り専用のプロパティで、イベント発生時に <kbd>alt</kbd> キー（macOS では <kbd>Option</kbd> または <kbd>⌥</kbd>）が押されたか (`true`) または押されていないか (`false`) を示す論理値です。

<kbd>Alt</kbd> キー自体が押されたり離されたりした際、このプロパティは、{{domxref("Element/keydown_event", "keydown")}} イベントでは `true` となり、{{domxref("Element/keyup_event", "keyup")}} イベントでは `false` となります。これは、どちらのイベントも状態の変化の後に発生するためです。

## 値

論理値です。

## 例

```html
<p>
  ALT キーを押したまま、または押さずに、任意の文字キーを押してください。<br />
  また、 SHIFT キーと ALT キーを同時に使用することもできます。
</p>
<pre id="output"></pre>
```

```js
const output = document.getElementById("output");

function showChar(e) {
  output.textContent = `Key KeyDown: "${e.key}"
ALT key KeyDown: ${e.altKey}
`;
}

document.addEventListener("keydown", showChar);
```

{{EmbedLiveSample("examples", "", "400")}}

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{ domxref("KeyboardEvent") }}
