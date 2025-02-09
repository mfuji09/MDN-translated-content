---
title: "WebSocket: send() メソッド"
short-title: send()
slug: Web/API/WebSocket/send
l10n:
  sourceCommit: fb311d7305937497570966f015d8cc0eb1a0c29c
---

{{APIRef("WebSockets API")}}{{AvailableInWorkers}}

**`WebSocket.send()`** メソッドは、 WebSocket 接続を介してサーバーに送るために指定されたデータを、格納するために必要なバイト数だけ `bufferedAmount` の値を増加させながらキューに入れます。もしデータが送信できなかった場合（例えば、バッファリングが必要だが、バッファーが一杯であるなどの理由で）、ソケットは自動的に閉じられます。
接続が `CONNECTING` 状態のときに `send()` を呼び出すと、ブラウザーは例外を発生させます。接続が `CLOSING` または `CLOSED` の状態のときに `send()` を呼び出すと、ブラウザーはデータを暗黙に破棄します。

## 構文

```js-nolint
send(data)
```

### 引数

- `data`

  - : サーバーに送信するデータです。以下の何れかの型のデータを指定します。

    - `string`
      - : テキスト文字列。文字列は UTF-8 形式でバッファーに追加され、 `bufferedAmount` の値は UTF-8 の文字列を表すのに必要とされるバイト数だけ増えます。
    - {{jsxref("ArrayBuffer")}}
      - : 型付きの配列オブジェクトで使用される基本的なバイナリーデータを送信することができます。このバイナリーデータのコンテンツは，必要なバイト数だけ `bufferedAmount` の値を増やして、バッファーのキューに入れられます。
    - {{domxref("Blob")}}
      - : `Blob` を指定すると、バイナリーフレームで送信される blob の生データをキューに入れます（{{domxref("Blob.type")}} は無視されます）。
      `bufferedAmount` の値は、その生データのバイトサイズだけ増えます。
    - {{jsxref("TypedArray")}} または {{jsxref("DataView")}}
      - : [JavaScript の型付き配列](/ja/docs/Web/JavaScript/Guide/Typed_arrays)オブジェクトをバイナリーフレームとして送信することができます。このバイナリーデータのコンテンツは，必要なバイト数だけ `bufferedAmount` の値を増やして、バッファーのキューに入れられます。

### 返値

なし ({{jsxref("undefined")}})。

### 例外

- `InvalidStateError` {{domxref("DOMException")}}
  - : {{domxref("WebSocket/readyState", "WebSocket.readyState")}} が `CONNECTING` である場合に発生します。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}
