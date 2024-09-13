---
title: Symbol.split
slug: Web/JavaScript/Reference/Global_Objects/Symbol/split
l10n:
  sourceCommit: e2dd7ae35f27c814d6017b79dac87e23c7996837
---

{{JSRef}}

**`Symbol.split`** は静的データプロパティで、[ウェルノウンシンボル](/ja/docs/Web/JavaScript/Reference/Global_Objects/Symbol#ウェルノウンシンボル)である `Symbol.split` を表します。{{jsxref("String.prototype.split()")}} メソッドは第一引数から、文字列内で現在のオブジェクトに一致する場所を返すメソッドを、このシンボルで探します。

詳しくは、[`RegExp.prototype[Symbol.split]()`](/ja/docs/Web/JavaScript/Reference/Global_Objects/RegExp/Symbol.split) と {{jsxref("String.prototype.split()")}} を参照してください。s

{{EmbedInteractiveExample("pages/js/symbol-split.html", "taller")}}

## 値

ウェルノウンシンボル `Symbol.split` です。

{{js_property_attributes(0, 0, 0)}}

## 例

### 独自の逆方向の分割

```js
class ReverseSplit {
  [Symbol.split](string) {
    const array = string.split(" ");
    return array.reverse();
  }
}

console.log("Another one bites the dust".split(new ReverseSplit()));
// [ "dust", "the", "bites", "one", "Another" ]
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [`Symbol.split` (`core-js`)](https://github.com/zloirock/core-js#ecmascript-symbol)
- {{jsxref("Symbol.match")}}
- {{jsxref("Symbol.matchAll")}}
- {{jsxref("Symbol.replace")}}
- {{jsxref("Symbol.search")}}
- {{jsxref("String.prototype.split()")}}
- [`RegExp.prototype[Symbol.split]()`](/ja/docs/Web/JavaScript/Reference/Global_Objects/RegExp/Symbol.split)
