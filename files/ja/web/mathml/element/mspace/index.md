---
title: <mspace>
slug: Web/MathML/Element/mspace
l10n:
  sourceCommit: 67cbfbf7a408e7180137b286247025bc40716642
---

{{MathMLRef}}

**`<mspace>`** は [MathML](/ja/docs/Web/MathML) の要素で、空白を作るために使われます。空白のサイズは属性で指定します。

## 属性

この要素の属性は、[グローバル MathML 属性](/ja/docs/Web/MathML/Global_attributes)と共に以下の属性があります。

- `depth`
  - : [`<length-percentage>`](/ja/docs/Web/CSS/length-percentage) で、この空間の希望する（ベースライン以下の）空間を示します。
- `height`
  - : [`<length-percentage>`](/ja/docs/Web/CSS/length-percentage) で、この空間の希望する（ベースラインの上の）高さを示します。
- `width`
  - : [`<length-percentage>`](/ja/docs/Web/CSS/length-percentage) で、この空間の希望の幅を示します。

> **メモ:** `depth`、`height`、`width` 属性については、一部のブラウザーは[古い MathML における長さ](/ja/docs/Web/MathML/Values#mathml_における古い長さ)も受け入れることがあります。

## 例

```html-nolint
<math display="block">
  <mn>1</mn>
  <mspace depth="40px" height="20px" width="100px"
          style="background: lightblue;"/>
  <mn>2</mn>
</math>
```

{{EmbedLiveSample('Examples')}}

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{ MathMLElement("mpadded") }}
- {{ MathMLElement("mphantom") }}
