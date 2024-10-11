---
title: 色の使用
slug: Web/Accessibility/Understanding_WCAG/Perceivable/Use_of_color
l10n:
  sourceCommit: f6d04a43eadf5ab26a3488942dfb318b58234eb5
---

{{QuicklinksWithSubPages("Web/Accessibility/Understanding_WCAG")}}

[色のコントラスト](/ja/docs/Web/Accessibility/Understanding_WCAG/Perceivable/Color_contrast)は主に美的な選択であることが多いですが、ウェブサイトで色を使用することは、情報を伝達するために色を使用することに関連します。色の使用に関する WCAG ガイドライン 1.4.1 では、「情報を伝えたり、アクションを示したり、レスポンスを促したり、視覚的要素を判別したりする唯一の視覚的手段として色を使用しない」ことが要求されています。

## 解決策

情報を伝えるために、色に加えて別の要素を使用しましょう。例えば、形式の検証エラーを示すには、色だけでなく別のフォント属性によって関連するフィールドのラベルを変えることができます。アイコンやシンボルは、色だけでなく図形でも異なる形にしてください。

色覚障碍（「色覚異常」）を持つユーザーに対応するため、緑が「良い」値、赤が「悪い」値を示す「信号機」のような色遣いを使用する場合は注意が必要です。赤緑色覚異常のユーザーは赤と緑を判別するのが難しいので、これらの値を区別することができないかもしれません。「良い」と「悪い」を示すためには、追加の要素を使用することが必要です。この状況では純粋な赤と緑は避けてください。赤みがかったオレンジと青みがかった緑は色覚異常のユーザーには判別できますが、正常な色覚のユーザーには文化的な「良い」と「悪い」の意味を伝えることができます。一方の色がもう一方の色より濃かったり薄かったりするようにして[色のコントラスト](/ja/docs/Web/Accessibility/Understanding_WCAG/Perceivable/Color_contrast)をつけることは、この文脈でも役立ちます。

## 関連する WCAG 達成基準

- [1.4.1 色の使用 (A)](https://www.w3.org/TR/WCAG21/#use-of-color)
  - : 色は情報を伝えたり、行動を示したり、レスポンスを促したり、視覚的要素を判別するための唯一の視覚的手段として使用するべきではありません。

## 関連情報

- [Understanding Success Criterion 1.4.1: Use of Color](https://www.w3.org/WAI/WCAG21/Understanding/use-of-color.html)
- [色のコントラスト](/ja/docs/Web/Accessibility/Understanding_WCAG/Perceivable/Color_contrast)
- [色とそのコントラスト](/ja/docs/Learn/Accessibility/CSS_and_JavaScript#色とそのコントラスト)（アクセシビリティチュートリアル）
