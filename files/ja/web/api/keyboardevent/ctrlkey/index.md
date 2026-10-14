---
title: "KeyboardEvent: ctrlKey プロパティ"
short-title: ctrlKey
slug: Web/API/KeyboardEvent/ctrlKey
l10n:
  sourceCommit: 358daf81ac9cf3db999cc8af7aed81ef4ff0c3f6
---

{{APIRef("UI Events")}}

**`KeyboardEvent.ctrlKey`** は読み取り専用のプロパティで、このイベントが発生したときに <kbd>control</kbd> キーが押されていた (`true`) または押されていなかった (`false`) ことを表す論理値を返します。

<kbd>Control</kbd> キー自体が押されたり離されたりした際、このプロパティは、{{domxref("Element/keydown_event", "keydown")}} イベントでは `true` となり、{{domxref("Element/keyup_event", "keyup")}} イベントでは `false` となります。これは、どちらのイベントも状態の変化の後に発生するためです。

## 値

論理値です。

## 例

```html
<p>
  CTRL キーを押したまま、または押さずに、任意の文字キーを押してください。<br />
  また、 SHIFT キーと CTRL キーを同時に使用することもできます。
</p>
<pre id="output"></pre>
```

```js
const output = document.getElementById("output");

function showChar(e) {
  output.textContent = `Key KeyDown: "${e.key}"
CTRL key KeyDown: ${e.ctrlKey}
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
