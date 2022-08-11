---
title: Text
slug: Web/API/Text
translation_of: Web/API/Text
---
{{ ApiRef() }}

The **`Text`** interface represents the textual content of {{domxref("Element")}} or {{domxref("Attr")}}. If an element has no markup within its content, it has a single child implementing `Text` that contains the element's text. However, if the element contains markup, it is parsed into information items and `Text` nodes that form its children.

New documents have a single `Text` node for each block of text. Over time, more `Text` nodes may be created as the document's content changes. The {{domxref("Node.normalize()")}} method merges adjacent `Text` objects back into a single node for each block of text.

## 属性

- {{domxref("Text.isElementContentWhitespace")}} {{readonlyInline}}{{Deprecated_Inline}}
  - : Returns a {{domxref("Boolean")}} flag indicatingwhether or not the text node contains only whitespace.
- {{domxref("Text.wholeText")}} {{readonlyInline}}
  - : Returns a {{domxref("DOMString")}} containing the text of all `Text` nodes logically adjacent to this {{domxref("Node")}}, concatenated in document order.

## 构造函数

- {{domxref("Text.Text", "Text()")}} {{experimental_inline}}
  - : Returns a `Text` node with the parameter as its textual content.

## 方法

- {{domxref("Text.replaceWholeText")}} {{Deprecated_Inline}}
  - : Replaces the text of the current node and all logically adjacent nodes with the specified text.
- {{domxref("Text.splitText")}}
  - : Breaks the node into two nodes at a specified offset.

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("api.Text")}}

## 相关链接

- [The DOM interfaces index](/en-US/docs/DOM/DOM_Reference).
