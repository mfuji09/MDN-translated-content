---
title: "Window: cancelIdleCallback() method"
short-title: cancelIdleCallback()
slug: Web/API/Window/cancelIdleCallback
page-type: web-api-instance-method
browser-compat: api.Window.cancelIdleCallback
---

{{APIRef}}

The **`window.cancelIdleCallback()`** method cancels a callback
previously scheduled with {{domxref("window.requestIdleCallback()")}}.

## 構文

```js-nolint
cancelIdleCallback(handle)
```

### 引数

- `handle`
  - : The ID value returned by {{domxref("window.requestIdleCallback()")}} when the
    callback was established.

### 返値

None ({{jsxref("undefined")}}).

## 例

See our [complete example](/ja/docs/Web/API/Background_Tasks_API#example)
in the article [Cooperative Scheduling of Background Tasks API](/ja/docs/Web/API/Background_Tasks_API).

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}
