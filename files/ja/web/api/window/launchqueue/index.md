---
title: "Window: launchQueue プロパティ"
short-title: launchQueue
slug: Web/API/Window/launchQueue
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Window.launchQueue
---

{{APIRef("Launch Handler API")}}{{SeeCompatTable}}

The `launchQueue` read-only property of the {{domxref("Window")}} interface provides access to the {{domxref("LaunchQueue")}} class, which allows custom launch navigation handling to be implemented in a [progressive web app](/ja/docs/Web/Progressive_web_apps) (PWA), with the handling context signified by the [`launch_handler`](/ja/docs/Web/Manifest/launch_handler) manifest field `client_mode` value.

The custom launch navigation handling functionality is controlled by the properties of the {{domxref("LaunchParams")}} object passed into the {{domxref("LaunchQueue.setConsumer()")}} callback function.

## 値

A {{domxref("LaunchQueue")}} object instance.

## 例

```js
if ("launchQueue" in window) {
  window.launchQueue.setConsumer((launchParams) => {
    if (launchParams.targetURL) {
      const params = new URL(launchParams.targetURL).searchParams;

      // Assuming a music player app that gets a track passed to it to be played
      const track = params.get("track");
      if (track) {
        audio.src = track;
        title.textContent = new URL(track).pathname.substring(1);
        audio.play();
      }
    }
  });
}
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{domxref("Launch Handler API", "Launch Handler API", "", "nocode")}}
- [Launch Handler API: Control how your app is launched](https://developer.chrome.com/docs/web-platform/launch-handler/)
- {{domxref("Window.launchQueue")}}
- [Musicr 2.0](https://launch-handler.glitch.me/) demo app
