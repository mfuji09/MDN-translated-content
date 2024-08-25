---
title: "Navigator: scheduling プロパティ"
short-title: scheduling
slug: Web/API/Navigator/scheduling
l10n:
  sourceCommit: cfb7587e3e3122630ad6cbd94d834ecadbe0a746
---

{{SeeCompatTable}}{{APIRef("Prioritized Task Scheduling API")}}

**`scheduling`** は {{domxref("Navigator")}} インターフェイスの読み取り専用プロパティで、現在の文書の {{domxref("Scheduling")}} オブジェクトを返します。このオブジェクトは、スケジュールタスクを制御するためのメソッドやプロパティを提供します。

## 値

{{domxref("Scheduling")}} オブジェクトです。

## 例

完全な例については {{domxref("Scheduling.isInputPending()")}} のページを参照してください。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [Faster input events with Facebook's first browser API contribution](https://engineering.fb.com/2019/04/22/developer-tools/isinputpending-api/) on engineering.fb.com (2019)
- [Better JS scheduling with isInputPending()](https://developer.chrome.com/docs/capabilities/web-apis/isinputpending) on developer.chrome.com (2020)
- [Optimizing long tasks](https://web.dev/articles/optimize-long-tasks#yield_only_when_necessary) on web.dev (2022)
