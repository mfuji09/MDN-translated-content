---
title: window.mozAnimationStartTime
slug: Web/API/Animation/startTime
---
{{ ApiRef() }}

{{ non-standard_header() }}

### 概述

Returns the time, in milliseconds since the epoch, at which animations started now should be considered to have started. This value should be used instead of, for example, [`Date.now()`](/zh-cn/JavaScript/Reference/Global_Objects/Date/now), because this value will be the same for all animations started in this window during this refresh interval, allowing them to remain in sync with one another.

This also allows JavaScript-based animations to remain synchronized with CSS transitions and SMIL animations triggered during the same refresh interval.

### 语法

```plain
time = window.mozAnimationStartTime;
```

### 规范

不属于任何规范。

### 相关链接

- {{ domxref("window.requestAnimationFrame()") }}
- {{ domxref("window.onmozbeforepaint") }}
