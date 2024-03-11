---
title: "CanvasRenderingContext2D: lineDashOffset プロパティ"
short-title: lineDashOffset
slug: Web/API/CanvasRenderingContext2D/lineDashOffset
l10n:
  sourceCommit: 6e0d822711793e8672d2ebfeea779890525f7529
---

{{APIRef}}

**`CanvasRenderingContext2D.lineDashOffset`** はキャンバス 2D API のプロパティで、線のダッシュオフセット、または「フェーズ」を設定します。

> **メモ:** 線は {{domxref("CanvasRenderingContext2D.stroke()", "stroke()")}} メソッドを呼び出すことで描画します。

## 値

線のダッシュオフセット量を指定する浮動小数点値。既定値は `0.0` です。

## 例

### 線ダッシュをオフセットする

この例では 2 本の破線を描画します。最初のものはダッシュオフセットがありません。 2 つ目のダッシュオフセットは 4 です。

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

ctx.setLineDash([4, 16]);

// Dashed line with no offset
ctx.beginPath();
ctx.moveTo(0, 50);
ctx.lineTo(300, 50);
ctx.stroke();

// Dashed line with offset of 4
ctx.beginPath();
ctx.strokeStyle = "red";
ctx.lineDashOffset = 4;
ctx.moveTo(0, 100);
ctx.lineTo(300, 100);
ctx.stroke();
```

#### 結果

ダッシュオフセットのある線は赤で描画されます。

{{ EmbedLiveSample('Offsetting_a_line_dash', 700, 180) }}

### アリの行進

[アリの行進](https://en.wikipedia.org/wiki/Marching_ants)効果はコンピューターグラフィックの選択ツールに多く見られるアニメーション技法です。選択範囲の境界をアニメーションさせることで、ユーザーが選択範囲の境界と画像の背景を見分けやすくします。

```html hidden
<canvas id="canvas"></canvas>
```

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
let offset = 0;

function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.setLineDash([4, 2]);
  ctx.lineDashOffset = -offset;
  ctx.strokeRect(10, 10, 100, 100);
}

function march() {
  offset++;
  if (offset > 5) {
    offset = 0;
  }
  draw();
  setTimeout(march, 20);
}

march();
```

{{ EmbedLiveSample('Marching_ants', 700, 180) }}

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- このプロパティを定義しているインターフェイス: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.getLineDash()")}}
- {{domxref("CanvasRenderingContext2D.setLineDash()")}}
- [スタイルと色の適用](/ja/docs/Web/API/Canvas_API/Tutorial/Applying_styles_and_colors)
