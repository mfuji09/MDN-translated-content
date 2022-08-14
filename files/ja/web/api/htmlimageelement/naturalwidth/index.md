---
title: HTMLImageElement.naturalWidth
slug: Web/API/HTMLImageElement/naturalWidth
page-type: web-api-instance-property
tags:
  - API
  - HTML
  - HTML DOM
  - HTMLImageElement
  - Intrinsic Width
  - Intrinsic size
  - プロパティ
  - リファレンス
  - naturalWidth
  - size
  - width
browser-compat: api.HTMLImageElement.naturalWidth
---
{{APIRef("HTML DOM")}}

{{domxref("HTMLImageElement")}} インターフェイスの
**`naturalWidth`** プロパティは読み取り専用で、画像の本来の（自然な）密度補正された幅を{{Glossary("CSS pixel", "CSS ピクセル数")}}で返します。

これは，何も制約を受けずに描画した場合の画像の幅です。画像の幅を指定しなかった場合、または画像の幅を制限するか明示するコンテナー内に画像を配置する場合、この値は画像の幅を CSS で指定されたピクセル数で表します。

対応する {{domxref("HTMLImageElement.naturalHeight", "naturalHeight")}} メソッドは、画像の自然な高さを返します。

> **Note:** ほとんどの場合、自然な幅とは、サーバーから送信された画像の実際の幅です。とはいえ、ブラウザーは画像をレンダラーにプッシュする前に画像を修正することができます。たとえば、 Chrome は[ローエンド端末で画像の解像度を低下させる](https://bugs.chromium.org/p/chromium/issues/detail?id=1187043#c7)などです。このような場合、 `naturalWidth` はそのようなブラウザーの介入によって修正された画像の幅を自然な幅とみなして、この値を返します。

## 値

画像の幅を CSS ピクセル単位で表した整数値。これは、画像に制約や特定の値が設定されていない場合に、画像が自然に描画される幅です。この自然な幅は、 {{domxref("HTMLImageElement.width", "width")}} とは異なり、表示されている端末のピクセル密度に合わせて補正されます。

画像に含まれる幅が指定されていない場合や、この情報を取得するための画像データが存在しない場合など、幅が利用できない場合は、 `naturalHeight` は 0 を返します。

## 例

[`HTMLImageElement.naturalHeight`](/ja/docs/Web/API/HTMLImageElement/naturalHeight#example) は、画像を「密度調整された」自然のサイズと、ページの CSS やその他の要素によって変化した表示サイズの両方で表示するコードの例として参照してください。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}
