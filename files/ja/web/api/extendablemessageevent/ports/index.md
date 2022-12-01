---
title: ExtendableMessageEvent.ports
slug: Web/API/ExtendableMessageEvent/ports
---

{{APIRef("Service Workers API")}}

{{domxref("ExtendableMessageEvent")}} インターフェイスの **`ports`** 読み取り専用プロパティは、関連するメッセージチャンネル（メッセージが送信されるチャンネル）のポートを表す {{domxref("MessagePort")}} オブジェクトを含む配列を返します。

## 構文

```
var myPorts = extendableMessageEvent.ports;
```

### 値

{{domxref("MessagePort")}} オブジェクトの配列。

## 例

次のコードをサービスワーカー内で使用して、{{domxref("PushMessageData")}} を介して受信したデータを[チャンネルメッセージ](/ja/docs/Web/API/Channel_Messaging_API)を介してメインコンテキストに送信することにより、プッシュメッセージに応答する場合、`onmessage` のイベントオブジェクトは `ExtendableMessageEvent` になります。

```js
var port;

self.addEventListener('push', function(e) {
  var obj = e.data.json();

  if(obj.action === 'subscribe' || obj.action === 'unsubscribe') {
    port.postMessage(obj);
  } else if(obj.action === 'init' || obj.action === 'chatMsg') {
    port.postMessage(obj);
  }
});

self.onmessage = function(e) {
  port = e.ports[0];
}
```

## 仕様

{{Specifications}}

## ブラウザーの互換性

{{Compat("api.ExtendableMessageEvent.ports")}}

## 関連情報

- [Service worker の使用](/ja/docs/Web/API/Service_Worker_API/Using_Service_Workers)
- [サービスワーカーの基本的なコード例](https://github.com/mdn/sw-test)（英語）
- [ServiceWorker の準備はできていますか？](https://jakearchibald.github.io/isserviceworkerready/)（英語）
- [Channel Messaging](/ja/docs/Web/API/Channel_Messaging_API)
