---
title: shape()
slug: Web/CSS/Reference/Values/basic-shape/shape
l10n:
  sourceCommit: 33094d735e90b4dcae5733331b79c51fee997410
---

**`shape()`** は [CSS の関数](/ja/docs/Web/CSS/Reference/Values/Functions)で、{{cssxref("clip-path")}} および {{cssxref("offset-path")}} プロパティの図形を定義するために使用されます。これは、図形のパスを定義する一連のシェイプコマンドと開始点を組み合わせたものです。`shape()` 関数は、{{cssxref("basic-shape")}} データ型のメンバーです。

## 構文

```css
/* <fill-rule> */
clip-path: shape(nonzero from 0 0, line to 10px 10px);

/* <move-command>, <line-command>, close */
offset-path: shape(from 10px 10px, move by 10px 5px, line by 20px 40%, close);

/* <hvline-command> */
offset-path: shape(from 10px 10px, hline by 50px, vline to 5rem);

/* <curve-command> */
offset-path: shape(
  from 10px 10px,
  curve to 80px 80px with 160px 1px / 20% 16px
);

/* <smooth-command> */
offset-path: shape(from 10px 10px, smooth to 100px 50pt);

/* <arc-command> */
offset-path: shape(
  from 5% 0.5rem,
  arc to 80px 1pt of 10% ccw large rotate 25deg
);

/* CSS 算術関数を使用 */
offset-path: shape(
  from 5px -5%,
  hline to 50px,
  vline by calc(0% + 160px),
  hline by 70.5px,
  close,
  vline by 60px
);

clip-path: shape(
  evenodd from 10px 10px,
  curve to 60px 20% with 40px 0,
  smooth to 90px 0,
  curve by -20px 60% with 10% 40px / 20% 20px,
  smooth by -40% -10px with -10px 70px,
  close
);
```

### 引数

- [`<fill-rule>`](/ja/docs/Web/SVG/Reference/Attribute/fill-rule) {{optional_inline}}
  - : 図形の重なり合う領域の塗りつぶし方法を指定します。使用可能な値は次のとおりです。
    - `nonzero`: ある点が図形の内側にあるとみなされるのは、点から描画された光線がパス区間を左から右へ通過する数が右から左へ通過する数よりも多く、その結果がゼロ以外の値となる場合です。これが、`<fill-rule>` が省略された場合のデフォルト値です。

    - `evenodd`: ある点が図形の内側にあるとみなされるのは、その点から引かれた光線が横切るパス区間の数が奇数の場合です。これは、光線が図形に入るたびに、同数の回数だけ出ていないことを意味し、対応する出口のない奇数の進入回数を示します。

    > [!WARNING]
    > `<fill-rule>` は {{cssxref("offset-path")}} では対応しておらず、使用するとプロパティが無効になります。

- `from <coordinate-pair>`
  - : 最初の `<shape-command>` の始点を、[参照ボックス](/ja/docs/Web/CSS/Guides/Shapes/Using_shape-outside#the_reference_box) の左上角から測定される座標のペアとして定義します。座標は空白区切りで指定される `<x> <y>` の {{cssxref("&lt;length-percentage&gt;")}} 値であり、それぞれ左オフセットと上オフセットを表します。パーセント値は、それぞれ要素の参照ボックスの幅と高さからの相対値です。この引数の後にカンマを追加します。

- `<shape-command>`
  - : 図形を定義する、カンマ区切りの1つ以上のコマンドのリストを指定します。構文は [SVG パスコマンド](/ja/docs/Web/SVG/Reference/Attribute/d#パスコマンド)と同様です。コマンドには `<move-command>`、`<line-command>`、`<hv-line-command>`、`<curve-command>`、`<smooth-command>`、`<arc-command>`、`close` があります。それぞれのコマンドの開始点は前回のコマンドの終了点であり、図形の最初の点は [`from <coordinate-pair>`](#from_coordinate-pair) 引数で定義されます。

#### シェイプコマンド

ほとんどのシェイプコマンドの構文は、`move` や `line` などのディレクティブとなるキーワードに、`by` または `to` キーワード、そして座標のセットが続く形式です。

- `by`: `<coordinate-pair>` がコマンドの開始点に対する相対座標（「相対」値）であることを示します。
- `to`: `<coordinate-pair>` が参照ボックスの左上角を基準とした相対座標であることを示します（「絶対」座標値）。

> [!NOTE]
> `<coordinate-pair>`内の座標がパーセント値で指定されている場合、その値は参照ボックスの対応する幅または高さを基準に計算されます。

次の `<shape-command>` が指定できます。

- `<move-command>`
  - : `move [by | to] <coordinate-pair>` の形で指定します。このコマンドはシェイプコマンドのリストに [MoveTo コマンド](/ja/docs/Web/SVG/Reference/Attribute/d#moveto_path_commands)を追加します。何も描画されず、代わりに次のコマンドの開始位置を指定します。`by` または `to` キーワードは、それぞれ `<coordinate-pair>` の点が相対座標か絶対座標かを指定します。`<移動コマンド>` が `close` コマンドに続く場合、次の図形またはサブパスの始点を識別します。

- `<line-command>`
  - : `line [by | to] <coordinate-pair>` の形で指定します。このコマンドはシェイプコマンドのリストに [LineTo コマンド](/ja/docs/Web/SVG/Reference/Attribute/d#lineto_path_commands) を追加します。コマンドの開始点から終了点まで直線を描画します。`by` または `to` キーワードは、`<coordinate-pair>` で指定される終了点が相対座標か絶対座標かをそれぞれ指定します。

- `<hv-line-command>`
  - : `[hline | vline] [by | to] <length-percentage>` の形で指定します。このコマンドは、シェイプコマンドのリストに水平線 (`hline`) または垂直線 (`vline`) の [LineTo コマンド](/ja/docs/Web/SVG/Reference/Attribute/d#lineto_path_commands)を追加します。`hline` では、コマンドの開始点から `<length-percentage>` で定義された `x` 位置まで、または `x` 位置から `<length-percentage>` で定義された `y` 位置まで水平線が描画されます。`vline` では、コマンドの始点から `<length-percentage>` で定義された `y` 位置まで、または `y` 位置から `<length-percentage>` で定義された `x` 位置まで垂直線が描画されます。`by` または `to` キーワードは、それぞれ相対的または絶対的な終了点を決定します。このコマンドは、単一の `<length-percentage>` で一方の座標値を指定し、もう一方の座標値がコマンドの開始点から変更されない `<line-command>` と同等です。

- `<curve-command>`
  - : Specified as `curve [by | to] <end-point> with <control-point> [/ <control-point>]`. This command adds a [Bézier curve command](/ja/docs/Web/SVG/Reference/Attribute/d#cubic_bézier_curve) to the list of shape commands. The `by` or `to` keyword determines whether the ending point of the curve, specified by the `<end-point>`, is relative or absolute.

    The `with` keyword specifies the control points of the Bézier curve as follows.
    - If only a single `<control-point>` is provided, the command draws a [quadratic Bézier curve](/ja/docs/Web/SVG/Reference/Attribute/d#quadratic_bézier_curve), which is defined by three points (the start point, control point, and end point).
    - If two `<control-point>` values are provided, the command draws a cubic Bézier curve, which is defined by four points (the start point, two control points, and the end point).

    Valid values for `<end-point>` include:
    - {{cssxref("&lt;position>")}} keywords or a `<coordinate-value-pair>`
      - : Can be used if the curve end point is absolute (specified using `to`).
    - `<coordinate-value-pair>`
      - : Can be used if the curve end point is relative (specified using `by`).

    Valid values for `<control-point>` include:
    - {{cssxref("&lt;position>")}}
      - : Specifies a position keyword. This value is valid only when the curve end point is absolute (specified using `to`).
    - `<coordinate-value-pair>`
      - : Specifies a pair of {{cssxref("&lt;length-percentage>")}} values that define coordinates.
    - `<relative-control-point>`
      - : Defines a `<coordinate-value-pair>` followed by the `from` keyword and one of the following keywords:
        - `start`
          - : Indicates that the control point is relative to the start point of the current command.
        - `end`
          - : Indicates that the control point is relative to the end point of the current command.
        - `origin`
          - : Indicates that the control point is relative to the top-left (origin) point of the container the shape is being drawn inside.
            > [!NOTE]
            > If the `<relative-control-point>` keywords are not specified, making the `<control-point>` a regular `<coordinate-value-pair>`, the coordinates are relative to the start of the curve. In other words, `start` is the default setting.

- `<smooth-command>`
  - : Specified as `smooth [by | to] <end-point> [with <control-point>]`. This command adds a smooth [Bézier curve command](/ja/docs/Web/SVG/Reference/Attribute/d#cubic_bézier_curve) to the list of shape commands. The `by` or `to` keyword determines whether the ending point of the curve, specified by the `<end-point>`, is relative or absolute.

    The `with` keyword specifies an optional control point for the Bézier curve:
    - If `with <control-point>` is omitted, the command draws a smooth quadratic Bézier curve, which uses the previous control point and the current endpoint to define the curve.
    - If the optional `with` keyword is included, it specifies a control points of the curve through `<control-point>`, drawing a smooth cubic Bézier curve defined by the previous control point, the current control point, and the current endpoint.

    Smooth curves ensure a continuous transition from the shape, while quadratic curves do not. Smooth quadratic curves maintain a seamless transition using a single control point, whereas smooth cubic curves provide a more refined transition using two control points.

    Valid values for the `<end-point>` and `<control-point>` components are the same as those for [`<curve-command>`](#curve-command).

- `<arc-command>`
  - : Specified as `arc [by | to] <coordinate-pair> of <length-percentage> [<length-percentage>] [<arc-sweep> | <arc-size> | rotate <angle>]`. This command adds an [elliptical arc curve command](/ja/docs/Web/SVG/Reference/Attribute/d#elliptical_arc_curve) to the list of shape commands. It draws an elliptical arc between a starting point and an ending point. The `by` or `to` keyword determines whether the ending point of the curve, specified by the first `<coordinate-pair>`, is relative or absolute, respectively.

    The elliptical arc curve command defines two possible ellipses, which intersect both the starting and ending points, and each can be traced clockwise or counterclockwise, resulting in four possible arcs depending on the arc size, direction, and angle. The `of` keyword specifies the size of the ellipse from which the arc is taken: the first `<length-percentage>` provides the horizontal radius of the ellipse, and the second `<length-percentage>` provides the vertical radius.

    Specify the following parameters to choose which of the four arcs to use:
    - `<arc-sweep>`: Indicates whether the desired arc is the one traced around the ellipse clockwise (`cw`) or counterclockwise (`ccw`). If omitted, this defaults to `ccw`.
    - `<arc-size>`: Indicates whether the desired arc is the larger (`large`) or smaller (`small`) of the two arcs. If omitted, this defaults to `small`.
    - `<angle>`: Specifies the angle, in degrees, by which to rotate the ellipse relative to the x-axis. A positive angle rotates the ellipse clockwise, and a negative angle rotates it counterclockwise. If omitted, this defaults to `0deg`.

    Special situations are handled as follows:
    - If only one `<length-percentage>` is provided, the same value is used for both the horizontal and vertical radii, effectively creating a circle. In this case, `<arc-size>` and `<angle>` have no affect.
    - If either radius is zero, the command is equivalent to a `<line-command>` to the ending point.
    - If either radius is negative, its absolute value is used instead.
    - If the horizontal and vertical radii don't describe an ellipse large enough to intersect both the starting point and ending points (after rotation by the specified `<angle>`), the radii are scaled up uniformly until the ellipse is just large enough to intersect both points.
    - If the starting and ending points of the arc lie on exactly opposite sides of the ellipse, there is only one possible ellipse and two possible arcs. In this case, `<arc-sweep>` specifies the arc to choose, and `<arc-size>` has no effect.

- `close`
  - : Adds a [ClosePath command](/ja/docs/Web/SVG/Reference/Attribute/d#closepath) to the list of shape commands, drawing a straight line from the current position (end of the last command) to the first point in the path defined in the `from <coordinate-pair>` parameter. To close the shape without drawing a line, include a `<move-command>` with the originating coordinates before the close command. If the `close` command is immediately followed by a `<move-command>`, it defines the starting point of the next shape or subpath.

## 解説

The `shape()` function allows you to define complex shapes. It is similar to the {{cssxref("basic-shape/path","path()")}} shape function in several ways:

- The `<fill-rule>` parameter in the `shape()` function works exactly like the same parameter in the `path()` function.
- The `shape()` function requires specifying one or more `<shape-command>`s, where each command uses an underlying [path command](/ja/docs/Web/SVG/Reference/Attribute/d#path_commands), such as [MoveTo](/ja/docs/Web/SVG/Reference/Attribute/d#moveto_path_commands), [LineTo](/ja/docs/Web/SVG/Reference/Attribute/d#lineto_path_commands), and [ClosePath](/ja/docs/Web/SVG/Reference/Attribute/d#closepath).

However, `shape()` offers several advantages over using `path()`:

- `shape()` uses standard CSS syntax, making it easier to create and modify shapes directly in your stylesheet. In comparison, `path()` uses the [SVG path](/ja/docs/Web/SVG/Reference/Element/path) syntax, which is less intuitive for those not familiar with SVG.
- `shape()` supports a variety of CSS units, including percentages, `rem`, and `em`. `path()`, on the other hand, defines shapes as a single string and limits units to `px`.
- `shape()` also allows the use of CSS math functions, like {{cssxref("calc")}}, {{cssxref("max")}}, and {{cssxref("abs")}}, providing more versatility when defining shapes.

## 形式文法

{{csssyntax}}

## 例

### `shape()` を使用してパスを定義

This example demonstrates how the `shape()` function can be used in the {{cssxref("offset-path")}} property to define the shape of the path an element can follow.

The first shape, `shape1`, follows a cubic Bézier curved path defined by the `curve to` command. Next, the `close` command draws a straight line from the curve's end point back to the initial point defined in the `from` command. Finally, `shape1` moves to its new position at `0px 150px` and then proceeds along a horizontal line.

The second shape, `shape2`, initially follows a horizontal line, then moves back to its starting position at `50px 90px`. Next, it follows a vertical line before closing the path back to the initial point.

Both shapes start with their original colors and gradually transition to `hotpink` by the end of the `move` animation, reverting to their initial color as the animation restarts. This cyclic color change provides you a visual cue about the animation's progression and restart.

```html hidden
<div class="container">
  Using <code>&lt;curve-command&gt;</code>
  <div class="shape shape1">>></div>
</div>

<div class="container">
  Using <code>&lt;move-command&gt;</code> and
  <code>&lt;hvline-command&gt;</code>
  <div class="shape shape2">>></div>
</div>
```

```css hidden
body {
  align-items: center;
  justify-content: center;
  display: flex;
}

.container {
  position: relative;
  display: inline-block;
  width: 250px;
  height: 250px;
  border: 2px dotted green;
  margin: 20px;
}

@supports not (offset-path: shape(from 0 0, move to 0 0)) {
  .container {
    display: none;
  }
  body::after {
    content: "Your browser doesn't support the `shape()` function yet.";
  }
}
```

```css
.shape {
  width: 50px;
  height: 50px;
  background: #2bc4a2;
  position: absolute;
  text-align: center;
  line-height: 50px;
  animation: move 6s infinite linear;
}

.shape1 {
  offset-path: shape(
    from 30% 60px,
    curve to 180px 180px with 90px 190px,
    close,
    move by 0px 150px,
    hline by 40%
  );
}

.shape2 {
  offset-path: shape(
    from 50px 90px,
    hline to 8em,
    move to 50px 90px,
    vline by 20%,
    close
  );
}

@keyframes move {
  0% {
    offset-distance: 0%;
  }
  100% {
    offset-distance: 100%;
    background-color: hotpink;
  }
}
```

#### 結果

{{EmbedLiveSample('Using shape() to define a path', '100%', 300)}}

### `shape()` を使用して要素の可視範囲を定義

This example demonstrates how the `shape()` function can be used in the {{cssxref("clip-path")}} property to create different shapes for the clipping region. The first shape (`shape1`) uses a triangle defined by straight lines. The second shape (`shape2`) includes curves and smooth transitions; it also illustrates the use of the `<move-command>` after the `close` command, which adds a rectangular shape to the clipping region.

```html hidden
<div class="container">
  <div class="shape shape1"></div>
</div>

<div class="container">
  <div class="shape shape2"></div>
</div>
```

```css hidden
body {
  align-items: center;
  justify-content: center;
  display: flex;
}

.container {
  position: relative;
  display: inline-block;
  width: 200px;
  height: 200px;
  margin: 20px;
  background-color: lightgray;
}

@supports not (clip-path: shape(from 0 0, move to 0 0)) {
  .container {
    display: none;
  }
  body::after {
    content: "Your browser doesn't support the `shape()` function yet.";
  }
}
```

```css
.shape {
  width: 100%;
  height: 100%;
  background: #2bc4a2;
  position: absolute;
  text-align: center;
  line-height: 50px;
}

/* Triangular clipping region */
.shape1 {
  clip-path: shape(from 0% 0%, line to 100% 0%, line to 50% 100%, close);
}

/* A Heart clipping region using curve and arc transitions
   and a box using hline and vline transitions */
.shape2 {
  clip-path: shape(
    from 20px 70px,
    arc to 100px 70px of 1% cw,
    arc to 180px 70px of 1% cw,
    curve to 100px 190px with 180px 130px,
    curve to 20px 70px with 20px 130px,
    close,
    move to 150px 150px,
    hline by 40px,
    vline by 40px,
    hline by -40px,
    close
  );
}
```

#### 結果

{{EmbedLiveSample('Using shape() to define the visible part of an element', '100%', 300)}}

### `shape()` を使用して相対制御点付きのカーブを描画

Like previous examples, this example also uses {{cssxref("clip-path")}} to create different shapes for the clipping regions of the elements. The shapes are specified using a combination of [`<curve-command>`](#curve-command) and [`<smooth-command>`](#smooth-command), and the control points are specified using [`<relative-control-point>`](#relative-control-point) values.

The first shape (`shape1`) draws two cubic Bézier curves.

- The first curve starts from the center of the left edge of the box and is drawn to a point `200px` along the x-axis — the center of the box's right edge. It uses one control point relative to the start of the curve and one control point relative to the origin (top-left of the box).
- The second curve starts from the center right of the box and is drawn `-200px` along the x-axis — the center of the box's left edge. It uses one control point relative to the origin and one control point relative to the start of the curve.

```html hidden live-sample___relative-control-points
<div class="container">
  <div id="shape1"></div>
  <div id="shape2"></div>
  <div id="shape3"></div>
</div>
```

```css hidden live-sample___relative-control-points
.container {
  display: flex;
  justify-content: center;
  gap: 20px;
}

@supports not (
  clip-path: shape(
      from center left,
      curve by 200px 0 with 50% -50% from start / 50% 0 from origin,
      curve by -200px 0 with 50% 100% from origin / -50% 50% from start,
      close
    )
) {
  .container {
    display: none;
  }
  body::after {
    content: "Your browser doesn't support `shape()` relative control points.";
  }
}
```

```css live-sample___relative-control-points
#shape1 {
  width: 200px;
  height: 200px;
  background: green;
  clip-path: shape(
    from center left,
    curve by 200px 0 with 50% -50% from start / 50% 0 from origin,
    curve by -200px 0 with 50% 100% from origin / -50% 50% from start,
    close
  );
}
```

The second shape (`shape2`) draws one quadratic Bézier curve and one cubic Bézier curve.

- The first curve starts from the center of the left edge of the box and is drawn to an absolute point `200px` from the origin along the x-axis and `100px` from the origin along the y-axis. It uses one control point relative to the start of the curve.
- The second curve starts from the previous curve's end point and is drawn to the center left of the box. It uses one control point relative to the start of the curve and one control point relative to the end.

```css live-sample___relative-control-points
#shape2 {
  width: 200px;
  height: 200px;
  background: purple;
  clip-path: shape(
    from center left,
    curve to 200px 100px with 50% -80% from start,
    curve to center left with 0% 70% from start / 20% 0% from end,
    close
  );
}
```

The third shape (`shape3`) draws one quadratic Bézier curve and one cubic Bézier curve using a `smooth` command.

- The first curve starts from the center of the left edge of the box and is drawn to a point `200px` along the x-axis. It uses one control point relative to the start of the curve.
- The second curve starts from the previous curve's end point and is drawn to the center of the box. It uses one control point relative to the start of the curve (the last control point of the previous curve) and one control point relative to the origin.

```css live-sample___relative-control-points
#shape3 {
  width: 200px;
  height: 200px;
  background: orangered;
  clip-path: shape(
    from center left,
    curve by 200px 0px with 50% -80% from start,
    smooth to center with 50% 100% from origin,
    close
  );
}
```

#### 結果

{{EmbedLiveSample('relative-control-points', '100%', 200)}}

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{cssxref("clip-path")}}
- {{cssxref("offset-path")}}
- [CSS シェイプ](/ja/docs/Web/CSS/Guides/Shapes)モジュール
- [シェイプの概要](/ja/docs/Web/CSS/Guides/Shapes/Overview)ガイド
- [基本シェイプ](/ja/docs/Web/CSS/Guides/Shapes/Using_shape-outside)ガイド
