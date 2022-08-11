---
title: FocusEvent
slug: Web/API/FocusEvent
tags:
  - API
  - DOM
  - DOM 事件
  - 事件
  - 参考
translation_of: Web/API/FocusEvent
---
{{APIRef("DOM Events")}}

**`FocusEvent`** 接口表示和焦点相关的事件比如 {{event("focus")}}, {{event("blur")}}, {{event("focusin")}}, 和 {{event("focusout")}}。

{{InheritanceDiagram}}

## 构造器

- {{domxref("FocusEvent.FocusEvent", "FocusEvent()")}}
  - : 使用给定的参数创建 `FocusEvent` 事件。

## 属性

_此接口从它的父级继承了属性 {{domxref("UIEvent")}}, 间接来自于 {{domxref("Event")}}_.

- {{domxref("FocusEvent.relatedTarget")}} {{readonlyInline}}
  - : {{domxref("EventTarget")}} 这个代表此次事件的次要目标。在一些案例中，例如切换浏览器 tab 标签时，为了安全的原因，这个属性可能会被设置为 `null` 。

## 方法

_此接口没有特殊的方法。它从父级 {{domxref("UIEvent")}} 继承方法_, 并间接从 {{domxref("Event")}} 继承方法。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("api.FocusEvent")}}

## 参见

- {{domxref("Event")}} 基接口
