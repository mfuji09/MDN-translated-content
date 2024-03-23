---
title: "HTMLSelectElement: checkValidity() メソッド"
short-title: checkValidity()
slug: Web/API/HTMLSelectElement/checkValidity
l10n:
  sourceCommit: 58269be5547b2e0b5b6f53a4c6eff6b13dfdf9bd
---

{{ APIRef("HTML DOM") }}

**`HTMLSelectElement.checkValidity()`** メソッドは、その要素に制約が設定されているかどうか、それを満足しているかどうかをチェックします。その要素が制約を満たしていない場合、ブラウザーはキャンセル可能な {{domxref("HTMLSelectElement/invalid_event", "invalid")}} イベントをその要素に送り、`false` を返します。

## 構文

```js-nolint
checkValidity()
```

### 引数

なし。

### 返値

要素の値に妥当性の問題がなければ `true` を返し、そうでなければ `false` を返します。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [フォームの検証](/ja/docs/Web/HTML/Constraint_validation)
