---
title: URL.username
slug: Web/API/URL/username
tags:
  - API
  - Property
  - Reference
  - URL
  - username
translation_of: Web/API/URL/username
---
{{ApiRef("URL API")}}

{{domxref("URL")}}接口的 username 属性是{{domxref("USVString")}} ，其中包含域名前指定的**`username`** 。

{{AvailableInWorkers}}

## 语法

```plain
string = object.username;
object.username = string;
```

### 值

一个 {{domxref("USVString")}}.

## 例子

```js
var url = new URL("https://anonymous:flabada@developer.mozilla.org/en-US/docs/Web/API/URL/username");
var user = url.username; // 返回：“anonymous”
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("api.URL.username")}}

## 参考

- 所属的 {{domxref("URL")}}接口。
