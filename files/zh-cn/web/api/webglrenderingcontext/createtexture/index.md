---
title: WebGLRenderingContext.createTexture()
slug: Web/API/WebGLRenderingContext/createTexture
translation_of: Web/API/WebGLRenderingContext/createTexture
---
{{APIRef("WebGL")}}

[WebGL API](/en-US/docs/Web/API/WebGL_API)的**`WebGLRenderingContext.createTexture()`** 方法创建并初始化了一个{{domxref("WebGLTexture")}} 目标。

## 语法

```plain
WebGLTexture gl.createTexture();
```

### 参数

无。

### 返回值

一个可以被任何图像绑定的 {{domxref("WebGLTexture")}} 目标

## 示例

另见 [Using textures in WebGL](/en-US/docs/Web/API/WebGL_API/Tutorial/Using_textures_in_WebGL)上的[WebGL tutorial](/en-US/docs/Web/API/WebGL_API/Tutorial)

### 创建一个纹理

```js
var canvas = document.getElementById('canvas');
var gl = canvas.getContext('webgl');
var texture = gl.createTexture();
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("api.WebGLRenderingContext.createTexture")}}

## 另见

- {{domxref("WebGLRenderingContext.bindTexture()")}}
- {{domxref("WebGLRenderingContext.deleteTexture()")}}
- {{domxref("WebGLRenderingContext.isTexture()")}}
- {{domxref("WebGLRenderingContext.texImage2D()")}}
