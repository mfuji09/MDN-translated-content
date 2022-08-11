---
title: WheelEvent.deltaZ
slug: Web/API/WheelEvent/deltaZ
translation_of: Web/API/WheelEvent/deltaZ
---
{{APIRef("DOM Events")}}

**`WheelEvent.deltaZ`** 只读属性是一个 `double` 类型值，声明 Z 轴滚动量以[`WheelEvent.deltaMode`](https://developer.mozilla.org/zh-CN/docs/Web/API/WheelEvent/deltaMode) 为单位。

## 语法

```plain
var dZ = event.deltaZ;
```

## 例子

```js
var syntheticEvent = new WheelEvent("syntheticWheel", {"deltaZ": 4, "deltaMode": 0});

console.log(syntheticEvent.deltaZ);
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("api.WheelEvent.deltaZ")}}

## 另见

- {{ event("wheel") }}
- {{domxref("WheelEvent")}}
