---
title: <display-internal>
slug: Web/CSS/display-internal
tags:
  - CSS 数据类型
  - CSS 显示
  - 参考
  - 显示内部
translation_of: Web/CSS/display-internal
---
一些布局模型，例如 `table` 和 `ruby`具有复杂的内部结构，具有他们的孩子和后代可以填充的几个不同的角色。此页面定义了那些“内部”显示值，这些值仅在该特定布局模式中具有意义。

## 语法

除非另有说明，否则使用这些显示值的元素的内部显示类型和外部显示类型都将设置为给定的关键字。

- `table-row-group`
  - : 这些元素的行为类似于[`<tbody>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tbody)HTML 元素。
- `table-header-group`
  - : 这些元素的行为类似于[`<thead>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/thead)HTML 元素。
- `table-footer-group`
  - : 这些元素的行为类似于[`<tfoot>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tfoot)HTML 元素。
- `table-row`
  - : 这些元素的行为类似于[`<tr>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tr)HTML 元素。
- `table-cell`
  - : 这些元素的行为类似于[`<td>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/td)HTML 元素。
- `table-column-group`
  - : 这些元素的行为类似于[`<colgroup>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/colgroup)HTML 元素。
- `table-column`
  - : 这些元素的行为类似于[`<col>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/col)HTML 元素。
- `table-caption`
  - : 这些元素的行为类似于[`<caption>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/caption)HTML 元素。
- `ruby-base` {{Experimental_Inline}}
  - : 这些元素的行为类似于[`<rb>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/rb)HTML 元素。
- `ruby-text` {{Experimental_Inline}}
  - : 这些元素的行为类似于[`<rt>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/rt)HTML 元素。
- `ruby-base-container` {{Experimental_Inline}}
  - : 这些元素的行为类似于[`<rbc>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/rbc)匿名框生成的 HTML 元素。
- `ruby-text-container` {{Experimental_Inline}}
  - : 这些元素的行为类似于[`<rtc>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/rtc)HTML 元素。

## [浏览器兼容性](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display-internal#Browser_compatibility)[编辑](https://developer.mozilla.org/en-US/docs/Web/CSS/display-internal$edit#Browser_compatibility)

### 支持表值

`table`, `table-cell`, `table-column`, `table-column-group`, `table-footer-group`, `table-header-group`, `table-row`, and `table-row-group`

{{Compat("css.properties.display.table_values", 10)}}

### 支持 ruby 值

`ruby`, `ruby-base`, `ruby-base-container`, `ruby-text`, and `ruby-text-container`

{{Compat("css.properties.display.ruby_values", 10)}}

## 另请参见

- {{CSSxRef("display")}}

  - {{CSSxRef("&lt;display-outside&gt;")}}
  - {{CSSxRef("&lt;display-inside&gt;")}}
  - {{CSSxRef("&lt;display-listitem&gt;")}}
  - {{CSSxRef("&lt;display-box&gt;")}}
  - {{CSSxRef("&lt;display-legacy&gt;")}}
