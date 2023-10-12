---
title: 色のコントラスト
slug: Web/Accessibility/Understanding_WCAG/Perceivable/Color_contrast
l10n:
  sourceCommit: f6d04a43eadf5ab26a3488942dfb318b58234eb5
---

{{QuicklinksWithSubPages("Web/Accessibility/Understanding_WCAG")}}

背景と前景のコンテンツ（つまり通常はテキスト）の[色のコントラスト](https://www.w3.org/TR/WCAG21/#dfn-contrast-ratio)は、確実に読みやすさを確保するのに十分なものでなければなりません。

様々な視覚能力に応じて読み取り可能なインターフェイスを設計する場合、 WCAG ガイドラインは以下のコントラスト比を推奨しています。

| コンテンツの種類                                                                 | 最小比率 (AA rating) | 強調比率 (AAA rating) |
| ------------------------------------------------------------------------------- | ------------------------- | --------------------------- |
| 本文テキスト                                                                       | 4.5 : 1                   | 7 : 1                       |
| 大きなテキスト（本文の 120-150% の大きさ）                               | 3 : 1                     | 4.5 : 1                     |
| アイコンやグラフなどのアクティブなユーザーインターフェイス部品とグラフィカルオブジェクト | 3 : 1                     | 未定義                 |

これらの比率は、非アクティブなコントロール、ロゴタイプ、純粋に装飾的なテキストなどの「付随的な」テキストには適用されません。

詳しくは後述の[解決策](#解決策)の節を参照してください。

サイトに良い色のコントラストを確保することは、すべてのユーザーにとって有益ですが、色覚異常や他にも似たような症状を持つユーザーにとっては特に有益です。これは、そのような症状のないユーザーほど明るい部分と暗い部分が見えにくく、輪郭や境界線、その他の細部が見えにくいためです。

ウェブサイトにクールなデザインがあるのは良いことですが、ユーザーがコンテンツを読むことができなければ、デザインに価値はありません。

## 例

単純な HTML と CSS のコードを見てみましょう。

```html
<div class="good">良いコントラスト</div>
<div class="bad">悪いコントラスト</div>
```

```css
div {
  /* ここで一般的な div のスタイルを定義 */
}

.good {
  background-color: #fae6fa;
}

.bad {
  background-color: #400064;
}
```

どちらのテキストも既定では黒色です。「良い」 `<div>` の背景は薄い紫色であり、テキストを読みやすくしています。

### 良いコントラスト

```html
<div class="good">良いコントラスト</div>
```

```css
div {
  font-family: sans-serif;
  text-align: center;
  font-size: 2rem;
  font-weight: bold;
  width: 250px;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 1px 1px 1px black;
}

.good {
  background-color: #fae6fa;
}
```

{{EmbedLiveSample('Good_Contrast', '100%', '100')}}

一方、「悪い」 `<div>` は背景がとても濃い紫色であるため、文字がとても読みにくくなっています：

### 悪いコントラスト

```html
<div class="bad">悪いコントラスト</div>
```

```css
div {
  font-family: sans-serif;
  text-align: center;
  font-size: 2rem;
  font-weight: bold;
  width: 250px;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 1px 1px 1px black;
}

.bad {
  background-color: #400064;
}
```

{{EmbedLiveSample('Bad_Contrast', '100%', '100')}}

## 解決策

ウェブサイトの配色を選ぶ際は、前景色と背景色のコントラストが高いものを選んでください。デザイン上の制約の中で、色のコントラストをできる限り良くしてください。理想的には AAA ランク（下記 1.4.6 参照）ですが、少なくとも AA ランク（下記 1.4.3 参照）は満たしてください。

動画やアニメーションなどテキスト以外のコンテンツを記載する場合は、 1.4.11 （下記参照）に従ってください。

色の選択をする際にコントラストを調べるには、 WebAIM の [Color Contrast Checker](https://webaim.org/resources/contrastchecker/) のようなツールを使用してください。

Firefox の開発者ツールを使って、色のコントラストをその場で調べることもできます。[アクセシビリティインスペクター](https://firefox-source-docs.mozilla.org/devtools-user/accessibility_inspector/index.html)のガイド、特に[アクセシビリティの問題を調べる](https://firefox-source-docs.mozilla.org/devtools-user/accessibility_inspector/index.html#check-for-accessibility-issues)の節を参照してください。説明の節のライブ例で使用してみてください。

## 関連する WCAG 達成基準

- [1.4.3 最小コントラスト (AA)](https://www.w3.org/TR/WCAG21/#contrast-minimum)

  - : 背景と前景のコンテンツの色のコントラストは、読みやすさを保証するための最小レベル以上でなければなりません：

    - テキストとその背景のコントラスト比は 4.5:1 以上であること。
    - 見出し（または単に大きい）テキストは、少なくとも 3:1 の比率を持つ必要があります。大きめのテキストとは、少なくとも 18pt、または 14pt の太字として定義されています。

- [1.4.6 拡張コントラスト (AAA)](https://www.w3.org/TR/WCAG21/#contrast-enhanced)

  - : これは基準1.4.3に従うことであり、基準1.4.3に基づいています。これは基準1.4.3に従うことであり、基準1.4.3に基づいています。

    - テキストとその背景のコントラスト比は 7:1 以上であるべきです。
    - 見出し（または単に大きい）テキストは、少なくとも 4.5:1 の比である必要があります。

- [1.4.11 テキスト以外のコントラスト (AA)](https://www.w3.org/TR/WCAG21/#non-text-contrast) （2.1 で追加）
  - : ユーザーインターフェイスコンポーネントとグラフィカルオブジェクトの色コントラスト比は最小で 3:1 であるべきです。

## 関連情報

- [色とそのコンテキスト](/ja/docs/Learn/Accessibility/CSS_and_JavaScript#色とそのコンテキスト)
- [複数のラベル](/ja/docs/Learn/Forms/How_to_structure_a_web_form#multiple_labels)
- [Understanding Non-Text Contrast](https://www.w3.org/WAI/WCAG21/Understanding/non-text-contrast.html)
