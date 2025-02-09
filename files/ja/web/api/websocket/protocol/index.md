---
title: "WebSocket: protocol プロパティ"
short-title: protocol
slug: Web/API/WebSocket/protocol
l10n:
  sourceCommit: fb311d7305937497570966f015d8cc0eb1a0c29c
---

{{APIRef("WebSockets API")}}{{AvailableInWorkers}}

**`WebSocket.protocol`** は読み取り専用のプロパティで、サーバーが選択した[サブプロトコル](/ja/docs/Web/API/WebSockets_API/Writing_WebSocket_servers#サブプロトコル)の名前を返します。これは {{domxref("WebSocket")}} オブジェクトが作成されるときに、引数の [`protocols`](/ja/docs/Web/API/WebSocket/WebSocket#protocols) で指定された文字列のいずれかになりますが、接続が確立されていない場合は、空文字列となります。

## 値

文字列です。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{httpheader("Sec-WebSocket-Protocol")}}
