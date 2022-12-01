---
title: SourceBuffer.buffered
slug: Web/API/SourceBuffer/buffered
---

{{APIRef("Media Source Extensions")}}{{SeeCompatTable}}

{{domxref("SourceBuffer")}} インターフェイスの **`buffered`** 読み取り専用プロパティは、`SourceBuffer` に現在バッファされている時間範囲を正規化された {{domxref("TimeRanges")}} オブジェクトとして返します。

## 構文

```
var myBufferedRange = sourceBuffer.buffered;
```

### 値

{{domxref("TimeRanges")}} オブジェクト。

## 例

未定

## 仕様

{{Specifications}}

## ブラウザーの互換性

{{Compat("api.SourceBuffer.buffered")}}

## 関連情報

- {{domxref("MediaSource")}}
- {{domxref("SourceBufferList")}}
