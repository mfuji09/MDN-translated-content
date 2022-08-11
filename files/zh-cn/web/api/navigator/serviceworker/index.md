---
title: Navigator.serviceWorker
slug: Web/API/Navigator/serviceWorker
translation_of: Web/API/Navigator/serviceWorker
---
{{APIRef("Service Workers API")}}

**`Navigator.serviceWorker`** 只读属性，返回 [关联文件](https://html.spec.whatwg.org/multipage/browsers.html#concept-document-window) 的 {{domxref("ServiceWorkerContainer")}} 对象，它提供对{{domxref("ServiceWorker")}} 的注册，删除，升级和通信的访问。。

## 语法

```plain
let workerContainerInstance = navigator.serviceWorker;
```

### 值

{{domxref("ServiceWorkerContainer")}}.

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat("api.Navigator.serviceWorker")}}

## 也可以看看

- [ServiceWorker API](/en-US/docs/Web/API/ServiceWorker_API)
- [Using Service Workers](/en-US/docs/Web/API/ServiceWorker_API/Using_Service_Workers)
