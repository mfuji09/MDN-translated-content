---
title: "Window: fence プロパティ"
short-title: fence
slug: Web/API/Window/fence
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Window.fence
---

{{SeeCompatTable}}{{APIRef("Fenced Frame API")}}

The `fence` read-only property of the {{domxref("Window")}} interface returns a {{domxref("Fence")}} object instance for the current document context.

`Fence` objects are only available to documents embedded inside {{htmlelement("fencedframe")}}s (loaded via {{domxref("FencedFrameConfig")}}s) or {{htmlelement("iframe")}}s (loaded via opaque URNs).

> **Note:** See [How do `<fencedframe>`s work?](/ja/docs/Web/API/Fenced_frame_API#how_do_fencedframes_work) for some description around `FencedFrameConfig`s and opaque URNs.

## 値

A {{domxref("Fence")}} object instance, or `null` if the document context does not have access to a {{domxref("Fence")}} object.

## 例

```js
window.fence.reportEvent({
  eventType: "click",
  eventData: JSON.stringify({ clickX: "123", clickY: "456" }),
  destination: ["buyer", "seller"],
});
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [Fenced frames](https://developer.chrome.com/docs/privacy-sandbox/fenced-frame/) on developer.chrome.com
- [The Privacy Sandbox](https://developer.chrome.com/docs/privacy-sandbox/) on developer.chrome.com
