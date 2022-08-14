---
title: 手机网页开发
slug: Web/Guide/Mobile
translation_of: Web/Guide/Mobile
---
本文主要是给出了网站开发所需的主要技术，这同样适用于手机设备。如果你正在寻找 Mozilla 火狐系统相关的项目，请参考[Firefox OS](/en/Mozilla/Firefox_OS) 。或者你可能会对[Firefox for Android](/en/Mozilla/Firefox_for_Android)感兴趣。

我们准备用两个章节来组织本文的内容，[designing for mobile devices](#Designing_for_mobile_devices) 和[cross-browser compatibility](#Cross-browser_development)。另外，这还有一篇 Jason Grlick 为 web 开发者写的指南 [mobile-friendliness](/en-US/docs/Web_Development/Mobile/Mobile-friendliness)。

## 手机设备设计

与台式机和笔记本相比，在硬件特性上手持设备有非常大的不同。当然通常他们的屏幕尺寸更小，另外一个特性是当用户旋转设备时，他们会在 portrait 和 landscape 模式下自动切换。旋转用户输入一般通过触屏。类似地理定位和排列方向这样在台式机上没有多大作用的 API，在手机用户使用你网站的时候有了全新的体验！

### 在更小的屏幕下工作

[响应式网页设计](/en/Web_Development/Responsive_Web_design)是一项让你的网站在手持设备上通过不同的使用环境进行自动适应的技术，通常来说体现在尺寸和屏幕的排列方向上。他包含下面的技术：

- 弹性化 CSS 布局设计，保证当浏览器窗口的尺寸变化时网页也能流畅地适应
- 根据设备屏幕的宽高，合理使用 css 媒体查询规则

[viewport meta 标签](/zh-CN/docs/)指定在用户设备的浏览器中的网页的缩放比例。

### 处理触摸屏

在触摸设备中你需要使用 dom 的 touch 事件。不再需要使用 css:hover 伪类；同时因为手指比鼠标要大的缘故，要将可点击元素做的更大一点。参见此文 [designing for touch screens](http://www.whatcreative.co.uk/blog/tips/designing-for-touch-screen/).

你可以使用[-moz-touch-enabled](/zh-CN/docs/Web/Guide/CSS/Media_queries#-moz-touch-enabled) media query 属性在可触摸设备上加载不同的 css。

### 优化图片

为了解决那些带宽小或者流量费用昂贵的用户，你可以通过根据用户的屏幕尺寸和分辨率加载合适的图片来优化图片的加载。你可以通过媒体查询来获取屏幕的 [height](/en/CSS/Media_queries#height)，[width](/en/CSS/Media_queries#width) 以及 [pixel ratio](/en/CSS/Media_queries#-moz-device-pixel-ratio)。

你也可以不使用图片，使用 css 属性像[gradients](/en/CSS/Using_CSS_gradients) 和 [shadows](/En/CSS/Box-shadow) 来实现更好的视觉效果。

### 移动 APIs

最后，你可以利用移动设备提供的新可能性， 例如 [orientation](/en/Detecting_device_orientation) 和 [geolocation](/En/Using_geolocation)。

## 跨浏览器开发

### 书写跨浏览器代码

创建能够完美工作在不同移动浏览器的 web sites:

- 请尽力避免使用特定浏览器的 features，例如 CSS 属性前的 vendor-prefixed(浏览器厂商前缀，也称浏览器引擎前缀)。例如-moz-为 Firefox|Firefox OS 浏览器引擎使用到的前缀。
- 如果你需要使用这些 features，请检查是否其它浏览器也有实现这些特性的版本。
- 对于不支持这些特性的浏览器，请提供一个可接受的 fallback。

例如，如果使用诸如 `-webkit-linear-gradient` 之类带有渲染器前缀的属性为一些文字设置了渐变背景，你最好能够将其他带有渲染器前缀的 `linear-gradient` 的相应属性一并添上。如果你没有这么做，请至少确保文字和默认的背景能形成对比。这样，即便在你没有指定 `linear-gradient` 的浏览器里，这个页面仍然是可用的。

请查看 [list of Gecko-specific properties](/en/CSS/CSS_Reference/Mozilla_Extensions) 以及 [WebKit-specific properties](/en/CSS/CSS_Reference/Webkit_Extensions) 这两个针对 Gecko 和 Webkit 浏览器的特殊前缀列表，以及这个由 Peter Beverloo 整理的 [table of vendor-specific properties](http://peter.sh/experiments/vendor-prefixed-css-property-overview/).

使用诸如 [CSS Lint](http://csslint.net/) 这样的工具可以帮助你查找这些问题， 诸如 [SASS](http://sass-lang.com/) 和 [LESS](http://lesscss.org/) 之类的预处理器可以帮助你处理这样的跨浏览器样式。

### 注意用户代理嗅探

我们推荐网站使用上面说到的方法来检测诸如屏幕尺寸和触摸屏之类的特定设备的特性，并且自动根据这些特性做出适配。但有时这样的办法并不那么管用，于是这是网站就会通过解析浏览器的 User Agent 来试图将桌面端，平板电脑端和手机端区分出来，并为不同的设备提供不同的内容。

如果你就是这样做的，请确保你的算法是可靠的，并且确保你的服务器没有因为没有正确解析某个浏览器的 User Agent 而给它提供了不合适的页面。请点击这里 [guide to using the user agent string to determine device type](/en/Browser_detection_using_the_user_agent#Mobile.2C_Tablet_or_Desktop) 查看关于 User Agent 解析的更多信息。

### 多浏览器中测试

在多个浏览器中测试你的网站。这意味着在多个平台测试—至少 iOS 和 Android。

- 使用 [iOS simulator](https://developer.apple.com/devcenter/ios/index.action) 在 IPhone 上测试移动版 Safari。
- 使用 [Android SDK](https://developer.android.com/sdk/index.html) 测试 Opera 和 Firefox。详细方法请点击 [running Firefox for Android using the Android emulator](https://wiki.mozilla.org/Mobile/Fennec/Android/Emulator) 查看。
