---
title: "Window: navigation プロパティ"
short-title: navigation
slug: Web/API/Window/navigation
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Window.navigation
---

{{APIRef("Navigation API")}}{{SeeCompatTable}}

The **`navigation`** read-only property of the {{domxref("Window")}} interface returns the current `window`'s associated {{domxref("Navigation")}} object.

This is the entry point for the {{domxref("Navigation API", "", "", "nocode")}}.

## 値

A {{domxref("Navigation")}} object instance.

## 例

```js
let currentNavEntries = window.navigation.entries();
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [Modern client-side routing: the Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [Navigation API explainer](https://github.com/WICG/navigation-api/blob/main/README.md)
- Domenic Denicola's [Navigation API live demo](https://gigantic-honored-octagon.glitch.me/)
