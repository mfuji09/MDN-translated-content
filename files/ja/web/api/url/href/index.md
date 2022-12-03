---
title: URL.href
slug: Web/API/URL/href
---

{{ApiRef("URL API")}}

{{domxref("URL")}} インターフェイスの **`href`** プロパティは、URL 全体を含む {{domxref("USVString")}} です。

{{AvailableInWorkers}}

## 構文

```
string = object.href;
object.href = string;
```

### 値

{{domxref("USVString")}}。

## 例

```js
var url = new URL('https://developer.mozilla.org/en-US/docs/Web/API/URL/href');
var result = url.href; // 戻り値: 'https://developer.mozilla.org/en-US/docs/Web/API/URL/href'
```

## 仕様

{{Specifications}}

## ブラウザーの互換性

{{Compat("api.URL.href")}}

## 関連情報

- {{domxref("URL")}} インターフェイスに属します。
