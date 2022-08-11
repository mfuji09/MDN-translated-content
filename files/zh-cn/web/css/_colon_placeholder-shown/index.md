---
title: ':placeholder-shown'
slug: Web/CSS/:placeholder-shown
translation_of: Web/CSS/:placeholder-shown
---
{{CSSRef}}{{SeeCompatTable}}

**`:placeholder-shown`** [CSS](/zh-CN/docs/Web/CSS) [伪类](/zh-CN/docs/CSS/Pseudo-classes) 在 {{htmlElement("input")}} 或 {{htmlElement("textarea")}} 元素显示 [placeholder text](/zh-CN/docs/Web/HTML/Element/input#attr-placeholder) 时生效。

```css
/* 选择所有显示占位符 (placeholder) 的元素 */
:placeholder-shown {
  border: 2px solid silver;
}
```

## 参数

```plain
:placeholder-shown
```

## 样例

### 基础样例

#### HTML

```html
<input placeholder="Type something here!">
```

#### CSS

```css
input {
  border: 2px solid black;
  padding: 3px;
}

input:placeholder-shown {
  border-color: silver;
}
```

#### 结果

{{EmbedLiveSample('Basic_example', 200, 60)}}

### 超出文本

在分辨率较小的设备上，输入框或者其他表单控件可能会变的很窄。这个选择器可以使得占位符文本缩短. 这个选择器经常和 {{cssxref("text-overflow")}} 一起使用。

#### HTML

```html
<input placeholder="Enter something into this field, if you please!">
```

#### CSS

```css
input:placeholder-shown {
  text-overflow: ellipsis;
}
```

#### 结果

{{EmbedLiveSample("Overflowing_text", 200, 60)}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("css.selectors.placeholder-shown")}}

## 参见

- The {{cssxref("::placeholder")}} pseudo-element styles the placeholder _itself_.
- Related HTML elements: {{HTMLElement("input")}}, {{HTMLElement("textarea")}}
- {{cssxref(":-moz-placeholder")}}, {{cssxref("::-moz-placeholder")}}
- [HTML forms](/zh-CN/docs/Learn/HTML/Forms)
