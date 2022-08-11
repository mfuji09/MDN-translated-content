---
title: focusout
slug: Web/API/Element/focusout_event
translation_of: Web/API/Element/focusout_event
original_slug: Web/Events/focusout
---
当元素即将失去焦点时，focusout 事件被触发。focusout 事件和 [blur](/zh-CN/docs/Web/Events/blur) 事件之间的主要区别在于后者不会冒泡。

## 基本信息

- Specification
  - : [DOM L3](http://www.w3.org/TR/DOM-Level-3-Events/#event-type-focusout)
- Interface
  - : {{domxref("FocusEvent")}}
- Bubbles
  - : Yes
- Cancelable
  - : No
- Target
  - : Element
- Default Action
  - : None.

## 属性

| Property                                 | Type                                               | Description                                |
| ---------------------------------------- | -------------------------------------------------- | ------------------------------------------ |
| `target` {{readonlyInline}}        | {{domxref("EventTarget")}}               | Event target losing focus.                 |
| `type` {{readonlyInline}}          | {{domxref("DOMString")}}                   | The type of event.                         |
| `bubbles` {{readonlyInline}}       | {{jsxref("Boolean")}}                       | Whether the event normally bubbles or not. |
| `cancelable` {{readonlyInline}}    | {{jsxref("Boolean")}}                       | Whether the event is cancellable or not.   |
| `relatedTarget` {{readonlyInline}} | {{domxref("EventTarget")}} (DOM element) | Event target receiving focus.              |

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("api.Element.focusout_event")}}

## 相关事件

- {{event("focus")}}
- {{event("blur")}}
- {{event("focusin")}}
- {{event("focusout")}}
