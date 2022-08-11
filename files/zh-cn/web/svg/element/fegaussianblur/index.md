---
title: feGaussianBlur
slug: Web/SVG/Element/feGaussianBlur
tags:
  - SVG
  - SVG 滤镜
  - 元素
  - 需要兼容性表
translation_of: Web/SVG/Element/feGaussianBlur
---
{{SVGRef}}

该滤镜对输入图像进行高斯模糊，属性{{ SVGAttr("stdDeviation") }}中指定的数量定义了钟形。

## 用法

{{svginfo}}

## 示例

### 简单示例

```html
<svg width="230" height="120"
 xmlns="http://www.w3.org/2000/svg"
 xmlns:xlink="http://www.w3.org/1999/xlink">

  <filter id="blurMe">
    <feGaussianBlur in="SourceGraphic" stdDeviation="5" />
  </filter>

  <circle cx="60"  cy="60" r="50" fill="green" />

  <circle cx="170" cy="60" r="50" fill="green"
          filter="url(#blurMe)" />
</svg>
```

该示例的结果如下所示：

{{EmbedLiveSample("Simple_example",232,124,"/files/4227/feGaussianBlur.png")}}

### 投影示例

```html
<svg width="120" height="120"
 xmlns="http://www.w3.org/2000/svg"
 xmlns:xlink="http://www.w3.org/1999/xlink">

  <filter id="dropShadow">
    <feGaussianBlur in="SourceAlpha" stdDeviation="3" />
    <feOffset dx="2" dy="4" />
    <feMerge>
        <feMergeNode />
        <feMergeNode in="SourceGraphic" />
    </feMerge>
  </filter>

  <circle cx="60"  cy="60" r="50" fill="green"
          filter="url(#dropShadow)" />
</svg>
```

该示例的结果如下所示：

{{EmbedLiveSample("Drop_shadow_example",125,124,"/files/4229/feGaussianBlur-dropshadow.png")}}

## 属性

### 全局属性

- [核心属性](/en/SVG/Attribute#Core) »
- [外观属性](/en/SVG/Attribute#Presentation) »
- [滤镜属性](/en/SVG/Attribute#Filter) »
- {{ SVGAttr("class") }}
- {{ SVGAttr("style") }}

### 专有属性

- {{ SVGAttr("in") }}
- {{ SVGAttr("stdDeviation") }}

## DOM 接口

该元素实现了[`SVGFEGaussianBlurElement`](/en/DOM/SVGFEGaussianBlurElement)接口。

## 参见

- {{ SVGElement("filter") }}
- {{ SVGElement("feBlend") }}
- {{ SVGElement("feColorMatrix") }}
- {{ SVGElement("feComponentTransfer") }}
- {{ SVGElement("feComposite") }}
- {{ SVGElement("feConvolveMatrix") }}
- {{ SVGElement("feDiffuseLighting") }}
- {{ SVGElement("feDisplacementMap") }}
- {{ SVGElement("feFlood") }}
- {{ SVGElement("feImage") }}
- {{ SVGElement("feMerge") }}
- {{ SVGElement("feMorphology") }}
- {{ SVGElement("feOffset") }}
- {{ SVGElement("feSpecularLighting") }}
- {{ SVGElement("feTile") }}
- {{ SVGElement("feTurbulence") }}
- [SVG 教程：滤镜效果](/en-US/docs/SVG/Tutorial/Filter_effects)
