---
title: "WebGLRenderingContext: bindAttribLocation() メソッド"
short-title: bindAttribLocation()
slug: Web/API/WebGLRenderingContext/bindAttribLocation
l10n:
  sourceCommit: eda49877b9078b24cd18f794470e5e225add9b94
---

{{APIRef("WebGL")}}

**`WebGLRenderingContext.bindAttribLocation()`** は [WebGL API](/ja/docs/Web/API/WebGL_API) のメソッドで、汎用頂点インデックスを属性変数にバインドします。

## 構文

```js-nolint
bindAttribLocation(program, index, name)
```

### 引数

- `program`
  - : バインドする {{domxref("WebGLProgram")}} オブジェクトです。
- `index`
  - : バインドする汎用頂点 インデックスの {{domxref("WebGL_API/Types", "GLuint")}} を指定します。
- `name`
  - : 汎用頂点インデックスにバインドする変数名を指定します。この名前は "webgl\_" または "\_webgl\_" から始めることはできません（WebGL で予約されています）。

### 返値

なし ({{jsxref("undefined")}})。

## 例

```js
gl.bindAttribLocation(program, colorLocation, "vColor");
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{domxref("WebGLRenderingContext.getActiveAttrib()")}}
- {{domxref("WebGLRenderingContext.getAttribLocation()")}}
- {{domxref("WebGLRenderingContext.getVertexAttrib()")}}
