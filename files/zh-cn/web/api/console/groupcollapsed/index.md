---
title: console.groupCollapsed
slug: Web/API/Console/groupCollapsed
translation_of: Web/API/Console/groupCollapsed
---
{{ ApiRef() }}

## 概述

在 [Web 控制台](../Tools/Web_Console)上创建一个新的分组。随后输出到控制台上的内容都会被添加一个缩进，表示该内容属于当前分组，直到调用[`console.groupEnd()`](../../Article_not_found?uri=zh-cn/DOM/console.groupEnd) 之后，当前分组结束。和 {{ domxref("console.group()") }}方法的不同点是，新建的分组默认是折叠的。用户必须点击一个按钮才能将折叠的内容打开。

## 语法

```plain
console.groupCollapsed();
```

## 参数

无

## 备注

在文档{{ domxref("console") }}中查看[在控制台中使用分组](/zh-cn/DOM/console#Using_groups_in_the_console),了解更多详细内容。

## 规范

不属于任何公开的规范

## 浏览器

{{Compat("api.console.groupCollapsed")}}

## 相关链接

- [Opera Dragonfly documentation: Console](http://www.opera.com/dragonfly/documentation/console/)
