---
title: "HTMLSourceElement: media プロパティ"
short-title: media
slug: Web/API/HTMLSourceElement/media
l10n:
  sourceCommit: 85fccefc8066bd49af4ddafc12c77f35265c7e2d
---

{{APIRef("HTML DOM")}}

**`media`** は {{domxref("HTMLSourceElement")}} インターフェイスのプロパティで、リソースの対象となるメディアを表す文字列です。値は[メディアクエリー](/ja/docs/Web/CSS/Guides/Media_queries/Using)であり、メディア種別、メディア特性、論理演算子をカンマ区切りで並べたものです。

このプロパティは、{{HTMLElement("source")}} 要素の `media` 属性を反映します。

## 値

文字列です。

## 例

```html
<video>
  <source
    id="el"
    src="largeVideo.mov"
    type="video/quicktime"
    media="screen and (width >= 600px)" />
</video>
```

```js
const el = document.getElementById("el");
console.log(el.media); // 出力結果: "screen and (width >= 600px)"
el.media = "(width >= 800px)"; // media の値を更新
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{domxref("HTMLSourceElement.type")}}
- {{domxref("HTMLSourceElement.sizes")}}
- {{domxref("HTMLSourceElement.src")}}
- {{domxref("HTMLSourceElement.srcset")}}
- {{htmlelement("source")}}
- {{htmlelement("picture")}}
- {{htmlelement("audio")}}
- {{htmlelement("video")}}
- [メディアクエリーの使用](/ja/docs/Web/CSS/Guides/Media_queries/Using)
