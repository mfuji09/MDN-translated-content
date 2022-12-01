---
title: PerformanceResourceTiming.fetchStart
slug: Web/API/PerformanceResourceTiming/fetchStart
---

{{APIRef("Resource Timing API")}}

**`fetchStart`** 読み取り専用プロパティは、ブラウザーがリソースの取得を開始する直前の {{domxref("DOMHighResTimeStamp","timestamp")}} を表します。

HTTP リダイレクトがある場合、このプロパティは、ユーザエージェントがリダイレクトの最後のリソースの取得を開始する直前の時間を返します。

{{AvailableInWorkers}}

## 構文

```
resource.fetchStart;
```

### 返値

ブラウザーがリソースの取得を開始する直前の {{domxref("DOMHighResTimeStamp")}}。

## 例

次の例では、すべての "`resource`" {{domxref("PerformanceEntry.entryType","type")}} イベントの\* `*Start` プロパティと `*End` プロパティの値が記録されます。

```js
function print_PerformanceEntries() {
  // Use getEntriesByType() to just get the "resource" events
  var p = performance.getEntriesByType("resource");
  for (var i=0; i < p.length; i++) {
    print_start_and_end_properties(p[i]);
  }
}
function print_start_and_end_properties(perfEntry) {
  // Print timestamps of the PerformanceEntry *start and *end properties
  properties = ["connectStart", "connectEnd",
                "domainLookupStart", "domainLookupEnd",
                "fetchStart",
                "redirectStart", "redirectEnd",
                "requestStart",
                "responseStart", "responseEnd",
                "secureConnectionStart"];

  for (var i=0; i < properties.length; i++) {
    // check each property
    var supported = properties[i] in perfEntry;
    if (supported) {
      var value = perfEntry[properties[i]];
      console.log("... " + properties[i] + " = " + value);
    } else {
      console.log("... " + properties[i] + " = NOT supported");
    }
  }
}
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat("api.PerformanceResourceTiming.fetchStart")}}
