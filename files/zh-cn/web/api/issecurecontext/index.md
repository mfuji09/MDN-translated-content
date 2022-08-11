---
title: isSecureContext
slug: Web/API/isSecureContext
tags:
  - API
  - Property
  - Reference
  - Window
  - WindowOrWorkerGlobalContext
  - Workers
  - isSecureContext
translation_of: Web/API/isSecureContext
original_slug: Web/API/WindowOrWorkerGlobalScope/isSecureContext
---
{{APIRef()}}{{SeeCompatTable}}

**`isSecureContext`** 是 `WindowOrWorkerGlobalScope` 的一个只读属性，返回一个布尔值，标识当前上下文是否安全，安全（true）或不安全（false）。

## 语法

```plain
var isItSecure = self.isSecureContext; // 或者直接使用 isSecureContext
```

### 类型

{{domxref("Boolean")}}.

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("api.isSecureContext")}}

## 参考

- [Secure contexts](/en-US/docs/Web/Security/Secure_Contexts)
