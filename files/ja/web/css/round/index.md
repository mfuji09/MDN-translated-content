---
title: round()
slug: Web/CSS/round
page-type: css-function
l10n:
  sourceCommit: 8ac73df2fbe2c88d8649fcb006dcde098616c723
---

{{CSSRef}}

**`round()`** は [CSS](/ja/docs/Web/CSS) の[関数](/ja/docs/Web/CSS/CSS_Functions)で、選択された丸め方法に基づいて丸めた数値を返します。

丸める値や間隔には[カスタム CSS プロパティ](/ja/docs/Web/CSS/--*)（`--my-property` など）を使用すべきです。これらが既知の値である場合は、 `round()` 関数を使用すると冗長になります。

## 構文

```css
width: round(var(--width), 50px);
width: round(up, 101px, var(--interval));
width: round(down, var(--height), var(--interval));
margin: round(to-zero, -105px, 10px);
```

### 引数

`round(<丸め方法>, valueToRound, roundingInterval)` 関数は、オプションの丸め方法、値（または数式）、丸められる値（または数式）を指定します。
`valueToRound` は、指定した丸め方法に従って、最も近い `roundingInterval` の整数倍に丸められます。

- `<丸め方法>`

  - : 丸め方法です。
    これは次の値のうちのいずれかを取ります。

    - `up`
      - : `valueToRound` を `roundingInterval` の最も近い整数倍に切り上げます（値が負の場合は「より正の方向」）。これは JavaScript の [`Math.ceil()`](/ja/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil) メソッドと同等です。
    - `down`
      - : `valueToRound` を `roundingInterval` の最も近い整数倍に切り下げます（値が負の場合は「より負の方向」）。これは JavaScript の [`Math.floor()`](/ja/docs/Web/JavaScript/Reference/Global_Objects/Math/floor) メソッドと同等です。
    - `nearest`（既定値）
      - : `valueToRound` を `roundingInterval` の整数倍のうち、高いほうまたは低いほうの最も近い値に丸めます（四捨五入）。
        `valueToRound` が上下両方の倍数のちょうど中間である場合（どちらも「最も近い」とは言えない場合）、切り上げになります。
        これは JavaScript の [`Math.round()`](/ja/docs/Web/JavaScript/Reference/Global_Objects/Math/round) メソッドと同等です。
    - `to-zero`
      - : `valueToRound` を `roundingInterval` のよりゼロの方向に近い直近の整数倍に丸めます（正の数ならば切り捨て、負の数ならば「より負ではない方向」）。 JavaScript の [`Math.trunc()`](/ja/docs/Web/JavaScript/Reference/Global_Objects/Math/trunc) メソッドです。

- `valueToRound`

  - : 丸められる値です。
    これは {{CSSxREF("&lt;number&gt;")}}、{{CSSxREF("&lt;dimension&gt;")}}、{{CSSxREF("&lt;percentage&gt;")}} のいずれか、またはこれらの値のいずれかに解決する数式でなければなりません。

- `roundingInterval`
  - : 丸められる値の間隔です。
    これは {{CSSxREF("&lt;number&gt;")}}、{{CSSxREF("&lt;dimension&gt;")}}、{{CSSxREF("&lt;percentage&gt;")}} のいずれか、またはこれらの値のいずれかに解決する数式でなければなりません。

### 返値

`valueToRound` の値を大小の `roundingInterval` の直近の整数倍に、 `丸め方法` に従って丸めたものです。

- `roundingInterval` が 0 の場合、結果は `NaN` となります。
- `valueToRound` と `roundingInterval` が両方とも `infinite` の場合、結果は `NaN` になります。
- `valueToRound` が無限大で、 `roundingInterval` が無限大ではない場合、結果は同じ `infinity` となります。
- `valueToRound` が無限大ではなく、 `roundingInterval` が無限大である場合、結果は丸め方式と `valueToRound` の符号によって変わります。

  - `up` - `valueToRound` が（ゼロではない）正の数の場合、 `+∞` を返します。 `valueToRound` が `0⁺` の場合、 `0⁺` を返します。それ以外の場合は、 `0⁻` を返します。
  - `down` - `valueToRound` が（ゼロではない）負の数の場合、 `−∞` を返します。 `valueToRound` が `0⁻` の場合、 `0⁻` を返します。それ以外の場合は、 `0⁺` を返します。
  - `nearest`, `to-zero` - `valueToRound` が正の数または `0⁺` である場合、 `0⁺` を返します。それ以外の場合は、 `0⁻` を返します。

- 引数の計算結果は {{CSSxREF("&lt;number&gt;")}}、{{CSSxREF("&lt;dimension&gt;")}}、{{CSSxREF("&lt;percentage&gt;")}} のいずれかに解決する可能性がありますが、同じ型でなければならず、そうでなければ関数が無効になります。結果は引数と同じ型になります。
- `valueToRound` がちょうど `roundingInterval` の整数倍であったとき、 `round()` はちょうど `valueToRound` に解決します（`valueToRound` が `0⁻` か `0⁺` かも維持されます）。そうでない場合、 `valueToRound` に「最も近い」可能性のある `roundingInterval` の整数倍の値は、下限の `roundingInterval`（`−∞`）と上限の `roundingInterval` （`+∞`）の 2 つになります。

### 形式文法

{{CSSSyntax}}

## 例

### 正の値の丸め

この例は、`round()` 関数の丸め方法が正の値に対してどのように機能するかを示しています。

下記 5 つのボックスのうち、 `round()` 関数は最後の 4 つの高さを設定するのに使用しています。
丸める値はそれぞれ 100px から 125px の間であり、丸め値はすべて 25px です。したがって、ボックスの高さは 125px に丸められるか、 100px に丸められます。

#### HTML

HTML は 5 つの `div` 要素を定義し、CSS によってボックスとしてレンダリングされます。
要素には、丸め方法、初期値、ボックスの最終的な予想高さを示すテキスト（括弧内）が含まれています。

```html
<div class="box box-1">height: 100px</div>
<div class="box box-2">up 101px (125px)</div>
<div class="box box-3">down 122px (100px)</div>
<div class="box box-4">to-zero 120px (100px)</div>
<div class="box box-5">nearest 117px (125px)</div>
```

#### CSS

```css hidden
body {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 50px;
}
```

すべてのボックスに適用されるCSSは下記に示します。丸め間隔に使用する、 `--rounding-interval` という名前の[カスタム CSS プロパティ](/ja/docs/Web/CSS/--*)を適用していることに注目して
ください。

```css
div.box {
  width: 100px;
  height: 100px;
  background: lightblue;
  padding: 5px;
  --rounding-interval: 25px;
}
```

左からみて最初の `div` は、特定の CSS ルールでターゲットにされていないため、既定で 100px の高さにします。
2、3、4 番目の `div` の CSS は下記に示すとおり、それぞれ round, up, down, to-zero です。

```css
div.box-2 {
  height: round(up, 101px, var(--rounding-interval));
}
div.box-3 {
  height: round(down, 122px, var(--rounding-interval));
}
div.box-4 {
  height: round(to-zero, 120px, var(--rounding-interval));
}
```

上記の例では、 `var()` 関数とカスタム CSS プロパティ `--rounding-interval` を使用して丸め間隔を示しています。

最後のボックスは丸め方法を指定せずに設定されているため、既定では最も近い値に丸められます。
この場合、 117px に最も近い区間は 125px なので、切り上げられます。
対照的に、ここでは丸め値と区間の両方にハードコードされた値を指定しています。
これは可能ですが、通常はこのようなことは行いません。なぜなら、結果がどうなるかすでにわかっているのに数値を丸める必要はないからです。

```css
div.box-5 {
  height: round(117px, 25px);
}
```

#### 結果

ブラウザーが CSS の `round()` 関数に対応している場合、テキストのコンテナーそのものが示すように、高さが丸められた 5 つの段組みが表示されるはずです。

{{EmbedLiveSample('Round positive values', '100%', '200px')}}

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{CSSxRef("mod")}}
- {{CSSxRef("rem")}}
