---
title: "Window: clearImmediate() method"
short-title: clearImmediate()
slug: Web/API/Window/clearImmediate
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.Window.clearImmediate
---

{{APIRef("HTML DOM")}} {{deprecated_header}}{{non-standard_header}}

This method clears the action specified by {{DOMxRef("window.setImmediate")}}.

## Syntax

```js-nolint
clearImmediate(immediateID)
```

### Parameters

- `immediateID`

  - : The ID returned by {{DOMxRef("window.setImmediate")}}.

### Return value

None ({{jsxref("undefined")}}).

## 例

```js
let immediateID = setImmediate(() => {
  // Run some code
});

document.getElementById("button").addEventListener(() => {
  clearImmediate(immediateID);
});
```

## 仕様書

Not part of any current specifications.
The [Efficient Script Yielding](https://w3c.github.io/setImmediate/#si-setImmediate)
specification is no longer being worked on.

## ブラウザーの互換性

{{Compat}}

## See also

- [Polyfill of `clearImmediate` in `core-js`](https://github.com/zloirock/core-js#setimmediate)
- {{DOMxRef("Window.setImmediate()")}}
