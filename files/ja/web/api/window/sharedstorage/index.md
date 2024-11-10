---
title: "Window: sharedStorage プロパティ"
short-title: sharedStorage
slug: Web/API/Window/sharedStorage
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Window.sharedStorage
---

{{APIRef("Shared Storage API")}}{{SeeCompatTable}}{{SecureContext_Header}}

The global read-only **`sharedStorage`** property returns the {{domxref("WindowSharedStorage")}} object for the current origin. This is the main entry point for writing data to shared storage using the [Shared Storage API](/ja/docs/Web/API/Shared_Storage_API).

> **Note:** `sharedStorage` is not available inside workers. It is implemented by {{domxref("Window")}} and is also available in shared storage worklets (see {{domxref("SharedStorageWorkletGlobalScope.sharedStorage")}}, which returns {{domxref("WorkletSharedStorage")}}).

## 値

A {{domxref("WindowSharedStorage")}} object instance.

## 例

```js
window.sharedStorage
  .set("ab-testing-group", "0")
  .then(console.log("Value saved to shared storage"));
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{domxref("WindowSharedStorage")}}
- [Shared Storage API](/ja/docs/Web/API/Shared_Storage_API)
