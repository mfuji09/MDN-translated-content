---
title: "WebSocket: readyState プロパティ"
short-title: readyState
slug: Web/API/WebSocket/readyState
l10n:
  sourceCommit: fb311d7305937497570966f015d8cc0eb1a0c29c
---

{{APIRef("WebSockets API")}}{{AvailableInWorkers}}

**`WebSocket.readyState`** は読み取り専用のプロパティで、 {{domxref("WebSocket")}} の「現在」の接続状態を返します。

## 値

数値であり、 {{domxref("WebSocket")}} インターフェイスで定義されている 4 つの定数のいずれかです。

- `WebSocket.CONNECTING` (0)
  - : ソケットの作成が完了した。接続は開かれていない。
- `WebSocket.OPEN` (1)
  - : 接続が開かれ、通信の準備ができている。
- `WebSocket.CLOSING` (2)
  - : 接続がが閉じる過程にある。
- `WebSocket.CLOSED` (3)
  - : 接続が閉じられたか、開くことができなかった。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}
