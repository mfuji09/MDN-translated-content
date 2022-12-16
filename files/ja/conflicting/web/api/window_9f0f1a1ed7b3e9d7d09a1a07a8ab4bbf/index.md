---
title: 'Window: vrdisplaypointerunrestricted イベント'
slug: conflicting/Web/API/Window_9f0f1a1ed7b3e9d7d09a1a07a8ab4bbf
original_slug: Web/API/Window/vrdisplaypointerunrestricted_event
---

{{APIRef("Window")}}{{Deprecated_Header}}{{Non-standard_Header}}

**`vrdisplaypointerunrestricted`** は [WebVR API](/ja/docs/Web/API/WebVR_API) のイベントで、 VR ディスプレイのポインター入力が[ポインターロックされた要素](/ja/docs/Web/API/Pointer_Lock_API)を介した消費を制限されなくなったときに、このイベントが発行されます。

> **メモ:** このイベントは古い [WebVR API](https://immersive-web.github.io/webvr/spec/1.1/) の一部でした。これは [WebXR 機器 API](https://immersive-web.github.io/webxr/) に置き換えられました。

このイベントはキャンセル不可で、バブリングしません。

## 構文

このイベント名を {{domxref("EventTarget.addEventListener", "addEventListener()")}} などのメソッドで使用するか、イベントハンドラープロパティを設定するかしてください。

```js
addEventListener('vrdisplaypointerunrestricted', (event) => { });

onvrdisplaypointerunrestricted = (event) => { };
```

## イベント型

{{domxref("VRDisplayEvent")}} です。 {{domxref("Event")}} を継承しています。

{{InheritanceDiagram("VRDisplayEvent")}}

## イベントプロパティ

_`VRDisplayEvent` は親オブジェクトである {{domxref("Event")}} からプロパティを継承しています。_

- {{domxref("VRDisplayEvent.display")}} {{Deprecated_Inline}} {{ReadOnlyInline}}
  - : このイベントに関連付けられた {{domxref("VRDisplay")}} です。
- {{domxref("VRDisplayEvent.reason")}} {{Deprecated_Inline}} {{ReadOnlyInline}}
  - : このイベントが発生した理由を人間可読な形で示します。

## 例

`vrdisplaypointerunrestricted` イベントは [`addEventListener`](/ja/docs/Web/API/EventTarget/addEventListener) メソッドで使用することができます。

```js
window.addEventListener('vrdisplaypointerunrestricted', () => {
  // ポインターロックを処理するコードを実行
});
```

または、 `onvrdisplaypointerunrestricted` イベントハンドラープロパティを使用してください。

```js
window.onvrdisplaypointerunrestricted = () => {
  // ポインターロックを処理するコードを実行
};
```

## 仕様書

このイベントは古い [WebVR API](https://immersive-web.github.io/webvr/spec/1.1/) の一部であり、これは [WebXR 機器 API](https://immersive-web.github.io/webxr/) で置き枯れられました。標準規格になる見込みはありません。

すべてのブラウザーが新しい [WebXR API](/ja/docs/Web/API/WebXR_Device_API/Fundamentals) を実装するまで、 [A-Frame](https://aframe.io/)、[Babylon.js](https://www.babylonjs.com/)、[Three.js](https://threejs.org/) などのフレームワークを使用するか、[ポリフィル](https://github.com/immersive-web/webxr-polyfill)を使用することが、すべてのブラウザーで動作する WebXR アプリを開発する上で推奨されます。[\[1\]](https://developer.oculus.com/documentation/web/port-vr-xr/)

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [WebVR API ホームページ](/ja/docs/Web/API/WebVR_API)
- <https://mixedreality.mozilla.org/> — Mozilla VR チームが提供するデモ、ダウンロード、その他のリソース。
