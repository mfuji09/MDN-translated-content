---
title: WheelEvent.deltaY
slug: Web/API/WheelEvent/deltaY
translation_of: Web/API/WheelEvent/deltaY
---
{{APIRef("DOM Events")}}

**`WheelEvent.deltaY`** 只读属性是一个 `double` 类型值，声明垂直滚动量以[`WheelEvent.deltaMode`](https://developer.mozilla.org/zh-CN/docs/Web/API/WheelEvent/deltaMode) 为单位。

## 语法

```plain
var dY = event.deltaY;
```

## 例子

```js
var syntheticEvent = new WheelEvent("syntheticWheel", {"deltaY": 4, "deltaMode": 0});

console.log(syntheticEvent.deltaY);
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("api.WheelEvent.deltaY")}}

## 另见

- {{ event("wheel") }}
- {{domxref("WheelEvent")}}
