---
title: FocusEvent
slug: Web/API/FocusEvent
l10n:
  sourceCommit: c45b0cf22b34da74660e7ca95140eff5ab2577d5
---

{{APIRef("UI Events")}}

**`FocusEvent`** はフォーカスに関するイベント、例えば {{domxref("Element/focus_event", "focus")}}、{{domxref("Element/blur_event", "blur")}}、{{domxref("Element/focusin_event", "focusin")}}、{{domxref("Element/focusout_event", "focusout")}} などを表します。

{{InheritanceDiagram}}

## コンストラクター

- {{domxref("FocusEvent.FocusEvent", "FocusEvent()")}}
  - : 指定した引数に基づいて、`FocusEvent` イベントを作成します。

## インスタンスプロパティ

_このインターフェイスは親である {{domxref("UIEvent")}} および間接的に {{domxref("Event")}} から、プロパティを継承しています_。

- {{domxref("FocusEvent.relatedTarget")}}
  - : このイベントのセカンダリーターゲットを表す {{domxref("EventTarget")}} です。一部の場合（タブ移動でページに出入りするときなど）では、セキュリティ上の理由からこのプロパティが `null` に設定されます。

## インスタンスメソッド

_このインターフェイスには固有のメソッドはありません。親である {{domxref("UIEvent")}} および間接的に {{domxref("Event")}} から、メソッドを継承しています。_

## イベントの順序

要素 A から要素 B にフォーカスが移動したとき、フォーカスイベントは以下の順序で発行されます。

1. `blur`: 要素 A がフォーカスを失った後に送られます。
2. `focusout`: `blur` イベントが送られた後で送られます。
3. `focus`: 要素 B がフォーカスを失った後に送られます。
4. `focusin`: `focus` イベントが送られた後で送られます。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{domxref("Event")}} 基本インターフェイス
