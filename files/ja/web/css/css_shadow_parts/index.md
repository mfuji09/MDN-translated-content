---
title: CSS シャドウパーツ
slug: Web/CSS/CSS_shadow_parts
l10n:
  sourceCommit: 835d6632d59993861a0458510402787f8a2c3cb3
---

{{CSSRef}}

**CSS シャドウパーツ**モジュールは、[シャドウルート](/ja/docs/Glossary/Shadow_tree)に設定する {{CSSXref("::part", "::part()")}} 擬似要素を定義します。この擬似要素を用いることで、シャドウホストがシャドウツリーで選択された要素をスタイル設定のために外部のページに公開することができます。

既定値では、シャドウツリー内の要素はそれぞれのシャドウルート内でのみスタイル設定できます。CSS シャドウパーツモジュールにより、カスタム要素を構成する {{HTMLElement("template")}} の子孫要素に [`part`](/ja/docs/Web/HTML/Global_attributes#part) 属性を記載し、シャドウツリーノードを `::part()` 擬似要素を介して外部のスタイル設定に公開することができます。

## リファレンス

### セレクター

- {{CSSXref("::part", "::part()")}}

### HTML 属性

- [`part`](/ja/docs/Web/HTML/Global_attributes#part)
- [`exportparts`](/ja/docs/Web/HTML/Global_attributes#exportparts)

### 定義

- {{glossary("Shadow tree", "シャドウツリー")}}

## ガイド

- [CSS 擬似要素](/ja/docs/Web/CSS/Pseudo-elements)

  - : すべての CSS 仕様と WebVTT で定義されている擬似要素のアルファベット順のリストです。

- [ウェブコンポーネント](/ja/docs/Web/API/Web_components)

  - : 再利用可能なカスタム要素やウェブコンポーネントを作成するための様々な API の概要。

## 関連概念

- HTML {{HTMLElement("template")}} 要素
- HTML {{HTMLElement("slot")}} 要素
- {{domxref("Element.part")}} プロパティ
- {{domxref("Element.shadowRoot")}} プロパティ
- {{domxref("Element.attachShadow()")}} メソッド
- {{domxref("ShadowRoot")}} インターフェイス
- [CSS スコープ](/ja/docs/Web/CSS/CSS_scoping) モジュール
  - {{CSSXref(":host")}}
  - {{CSSXref(":host_function", ":host()")}}
  - {{CSSXref(":host-context", ":host-context()")}}
  - {{CSSXref("::slotted")}}

## 仕様書

{{Specifications}}

## 関連情報

- [CSS 擬似要素](/ja/docs/Web/CSS/CSS_pseudo-elements)モジュール
- [CSS セレクター](/ja/docs/Web/CSS/CSS_selectors)モジュール
- [シャドウ DOM の使用](/ja/docs/Web/API/Web_components/Using_shadow_DOM)
- [Templates: Styling outside of the current scope](https://web.dev/learn/html/template/#styling_outside_of_the_current_scope) (web.dev, 2023)
