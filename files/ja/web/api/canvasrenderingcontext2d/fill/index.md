---
title: "CanvasRenderingContext2D: fill() メソッド"
short-title: fill()
slug: Web/API/CanvasRenderingContext2D/fill
l10n:
  sourceCommit: 1f216a70d94c3901c5767e6108a29daa48edc070
---

{{APIRef}}

**`CanvasRenderingContext2D.fill()`** はキャンバス 2D API のメソッドで、現在の、または与えられたパスを現在の {{domxref("CanvasRenderingContext2D.fillStyle", "fillStyle")}} で塗りつぶします。

## 構文

```js-nolint
fill()
fill(path)
fill(fillRule)
fill(path, fillRule)
```

### 引数

- `fillRule`

  - : 点が塗りつぶし領域の内側にあるか外側にあるかを判断するアルゴリズムです。
    取りうる値は次の通りです。

    - `nonzero`
      - : [非ゼロワインディングルール](https://en.wikipedia.org/wiki/Nonzero-rule)（英語）です。
        既定のルールです。
    - `evenodd`
      - : [偶数奇数ワインディングルール](https://en.wikipedia.org/wiki/Even%E2%80%93odd_rule)（英語）です。

- `path`
  - : 塗りつぶす {{domxref("Path2D")}} パスです。

### 返値

なし ({{jsxref("undefined")}})。

## 例

### 長方形の塗りつぶし

この例では、 `fill()` メソッドで長方形を塗りつぶします。

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.rect(10, 10, 150, 100);
ctx.fill();
```

#### 結果

{{ EmbedLiveSample('Filling_a_rectangle', 700, 180) }}

### パスと fillRule の指定

この例では、いくつかの交差する線を Path2D オブジェクトに保存しています。次に `fill()` メソッドを使ってオブジェクトをキャンバスに描画します。次に `fill()` メソッドを使ってオブジェクトをキャンバスに描画します。`"evenodd"` ルールを使うと、オブジェクトの中心に穴が空きます。既定では（"nonzero"` ルールで）穴も塗りつぶされます。

#### HTML

```html
<canvas id="canvas"></canvas>
```

#### JavaScript

```js
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

// パスを作成
let region = new Path2D();
region.moveTo(30, 90);
region.lineTo(110, 20);
region.lineTo(240, 130);
region.lineTo(60, 130);
region.lineTo(190, 20);
region.lineTo(270, 90);
region.closePath();

// パスを塗りつぶし
ctx.fillStyle = "green";
ctx.fill(region, "evenodd");
```

#### 結果

{{ EmbedLiveSample('Specifying_a_path_and_a_fillRule', 700, 180) }}

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- このメソッドを定義しているインターフェイス: {{domxref("CanvasRenderingContext2D")}}
- {{domxref("CanvasRenderingContext2D.fillStyle")}}
