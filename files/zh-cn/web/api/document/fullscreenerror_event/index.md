---
title: Document.onfullscreenerror
slug: Web/API/Document/fullscreenerror_event
---
{{ApiRef("Fullscreen API")}}

Document.onfullscreenerror 属性是一个事件处理器用于处理 {{event("fullscreenchange")}} 事件，在当前文档不能进入全屏模式，即使它被请求时触发。

## 语法

```plain
targetDocument.onfullscreenerror = fullscreenErrorHandler;
```

## 示例

```js
document.onfullscreenerror = function ( event ) {
  console.log("FULL SCREEN DENIED")
};

// requestFullscreen() 将会失败，因为它在事件处理器之外
document.documentElement.requestFullscreen();
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("api.Document.fullscreenerror_event")}}

## 相关文章

- {{event("fullscreenerror")}}
- {{domxref("Document.onfullscreenchange")}}
