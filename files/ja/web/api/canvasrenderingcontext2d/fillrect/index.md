---
title: "CanvasRenderingContext2D: fillRect() メソッド"
short-title: fillRect()
slug: Web/API/CanvasRenderingContext2D/fillRect
l10n:
  sourceCommit: 1f216a70d94c3901c5767e6108a29daa48edc070
---

{{APIRef}}

**`CanvasRenderingContext2D.fillRect()`** はキャンバス 2D API のメソッドで、塗りつぶした長方形を現在の {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}} に基づいて描きます。

このメソッドはキャンバスに直接描画を行い、現在のパスを変更しません。したがって、その後の {{domxref("CanvasRenderingContext2D.fill()", "fill()")}} または {{domxref("CanvasRenderingContext2D.stroke()", "stroke()")}} の呼び出しには影響しません。

## 構文

```js-nolint
fillRect(x, y, width, height)
```

`fillRect()` メソッドは塗りつぶした長方形を、 `(x, y)` を始点とし、 `width` と `height` でサイズを指定しで描画します。塗りつぶしのスタイルは、現在の `fillStyle` 属性によって決定されます。

### 引数

- `x`
  - : 長方形の開始位置の X 座標です。
- `y`
  - : 長方形の開始位置の Y 座標です。
- `width`
  - : 長方形の幅です。正の数であれば右方向、負の数であれば左方向です。
- `height`
  - : 長方形の高さです。正の数であれば下方向、負の数であれば上方向です。

### 返値

なし ({{jsxref("undefined")}})。

## 例

### 単純な塗りつぶした長方形

`fillRect()` メソッドを利用した簡単な使用例です。

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

長方形の左上は (20, 10) です。幅は 150 で高さは 100 です。

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.fillStyle = "green";
ctx.fillRect(20, 10, 150, 100);
```

#### 結果

{{ EmbedLiveSample('A_simple_filled_rectangle', 700, 180) }}

### キャンバス全体の塗りつぶし

このコードでは、キャンバス全体を長方形で塗りつぶします。これは、背景を作成し、その上に他のものを描画するのに便利です。このため、長方形の寸法は {{HtmlElement("canvas")}} 要素の `width` と `height` 属性に等しくなるように設定されています。

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.fillRect(0, 0, canvas.width, canvas.height);
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- このメソッドを定義しているインターフェイス: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.fillStyle")}}
- {{domxref("CanvasRenderingContext2D.clearRect()")}}
- {{domxref("CanvasRenderingContext2D.strokeRect()")}}
