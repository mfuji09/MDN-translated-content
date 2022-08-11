---
title: 相邻兄弟选择器
slug: Web/CSS/Adjacent_sibling_combinator
tags:
  - CSS
  - Selectors
translation_of: Web/CSS/Adjacent_sibling_combinator
---
{{CSSRef("Selectors")}}

**相邻兄弟选择器** (`+`) 介于两个选择器之间，当第二个元素*紧跟在*第一个元素之后，并且两个元素都是属于同一个父{{domxref("元素")}}的子元素，则第二个元素将被选中。

```css
/* 图片后面紧跟着的段落将被选中 */
img + p {
  font-weight: bold;
}
```

## 语法

```plain
former_element + target_element { style properties }
```

## 示例

### CSS

```css
li:first-of-type + li {
  color: red;
}
```

### HTML

```html
<ul>
  <li>One</li>
  <li>Two!</li>
  <li>Three</li>
</ul>
```

### 结果

- One
- Two!
- Three

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("css.selectors.adjacent_sibling")}}

## 参阅

- [通用兄弟选择器](/zh-CN/docs/Web/CSS/General_sibling_selectors)
