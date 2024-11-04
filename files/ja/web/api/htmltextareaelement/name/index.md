---
title: "HTMLTextAreaElement: name プロパティ"
short-title: name
slug: Web/API/HTMLTextAreaElement/name
l10n:
  sourceCommit: d064784c78ec30c87ec3c3d9681b147999fd782f
---

{{ApiRef("HTML DOM")}}

**`name`** は {{domxref("HTMLTextAreaElement")}} インターフェイスのプロパティで、この {{HTMLElement("textarea")}} 要素の名前を示します。これは、この要素の [`name`](/ja/docs/Web/HTML/Element/textarea#name) 属性を反映します。

## 値

この要素の名前を表す文字列です。

## 例

```js
const textareaElement = document.querySelector("#message");
console.log(`Element's name: ${textareaElement.name}`);
textareaElement.name = "response"; // 要素の name を設定または更新
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{domxref("HTMLTextAreaElement.value")}}
- {{domxref("HTMLTextAreaElement.textLength")}}
