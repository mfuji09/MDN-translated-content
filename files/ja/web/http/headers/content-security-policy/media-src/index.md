---
title: 'CSP: media-src'
slug: Web/HTTP/Headers/Content-Security-Policy/media-src
tags:
  - CSP
  - Content-Security-Policy
  - Directive
  - HTTP
  - Media
  - Reference
  - Security
  - media-src
  - source
browser-compat: http.headers.Content-Security-Policy.media-src
translation_of: Web/HTTP/Headers/Content-Security-Policy/media-src
---
{{HTTPSidebar}}

HTTP の {{HTTPHeader("Content-Security-Policy")}} (CSP) における **`media-src`** ディレクティブは、 {{HTMLElement("audio")}} および {{HTMLElement("video")}} 要素を使用して読み込むメディアの有効なソースを指定します。

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">CSP バージョン</th>
      <td>1</td>
    </tr>
    <tr>
      <th scope="row">ディレクティブ種別</th>
      <td>{{Glossary("Fetch directive", "フェッチディレクティブ")}}</td>
    </tr>
    <tr>
      <th scope="row">{{CSP("default-src")}} による代替</th>
      <td>
        あり。このディレクティブがない場合、ユーザーエージェントは `default-src` ディレクティブを探します。
      </td>
    </tr>
  </tbody>
</table>

## 構文

`media-src` ポリシーには、 1 つ以上のソースが許可されています。

```http
Content-Security-Policy: media-src <source>;
Content-Security-Policy: media-src <source> <source>;
```

### ソース

`<source>` は、 [CSP ソース値](/ja/docs/Web/HTTP/Headers/Content-Security-Policy/Sources#ソース)にあるいずれかの値を取ることができます。

なお、この同じ値のセットはすべての{{Glossary("fetch directive", "フェッチディレクティブ")}}（と [他の多くのディレクティブ](/ja/docs/Web/HTTP/Headers/Content-Security-Policy/Sources#関連ディレクティブ)）で使用できます。

## 例

## 違反例

この CSP ヘッダーがある場合、

```http
Content-Security-Policy: media-src https://example.com/
```

以下の {{HTMLElement("audio")}}, {{HTMLElement("video")}}, {{HTMLElement("track")}} の各要素はブロックされ、読み込まれません。

```html
<audio src="https://not-example.com/audio"></audio>

<video src="https://not-example.com/video">
  <track kind="subtitles" src="https://not-example.com/subtitles">
</video>
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{HTTPHeader("Content-Security-Policy")}}
- {{HTMLElement("audio")}}, {{HTMLElement("video")}}, {{HTMLElement("track")}}
