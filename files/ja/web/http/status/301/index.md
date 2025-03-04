---
title: 301 Moved Permanently
slug: Web/HTTP/Status/301
l10n:
  sourceCommit: 5b20f5f4265f988f80f513db0e4b35c7e0cd70dc
---

{{HTTPSidebar}}

HTTP の **`301 Moved Permanently`** [リダイレクトレスポンス](/ja/docs/Web/HTTP/Status#リダイレクトメッセージ)ステータスコードは、リクエストされたリソースが {{HTTPHeader("Location")}} ヘッダーで示された URL へ完全に移動したことを示します。

このステータスを受信したブラウザーは、自動的に `Location` ヘッダー内の URL のリソースをリクエストし、ユーザーを新しいページにリダイレクトします。
このレスポンスを受け取った検索エンジンは、リダイレクトされたリソースに元の URL へのリンク属性を付与し、 {{Glossary("SEO")}} のランキングを新しい URL に渡します。

> [!NOTE]
> [フェッチ標準](https://fetch.spec.whatwg.org/#http-redirect-fetch)では、ユーザーエージェントが `301` を {{HTTPMethod("POST")}} リクエストに対するレスポンスとして受け取った場合、 HTTP [仕様書](#仕様書)に従って、その後のリダイレクトリクエストでは {{HTTPMethod("GET")}} メソッドを使用します。
> ユーザーエージェントによるリクエストの変更を避けるには、代わりに {{HTTPStatus("308", "308 Permanent Redirect")}} を使用してください。 `308` レスポンスは、その後のメソッドの変更が禁止されています。

## ステータス

```http
301 Moved Permanently
```

## 例

### クライアントリクエスト

次の {{HTTPMethod("GET")}} リクエストは、 `301` リダイレクトが返されるリソースに対して行われます。

```http
GET /en-US/docs/AJAX HTTP/2
Host: developer.mozilla.org
User-Agent: curl/8.6.0
Accept: */*
```

レスポンスには `301` ステータスと、リソースが移動した URL を示す {{HTTPHeader("Location")}} ヘッダーが含まれます。

```http
HTTP/2 301
cache-control: max-age=2592000,public
location: /en-US/docs/Learn_web_development/Core/Scripting/Network_requests
content-type: text/plain; charset=utf-8
date: Fri, 19 Jul 2024 12:57:17 GMT
content-length: 97

Moved Permanently. Redirecting to /en-US/docs/Learn_web_development/Core/Scripting/Network_requests
```

## 仕様書

{{Specifications}}

## 関連情報

- [HTTP のリダイレクト](/ja/docs/Web/HTTP/Redirections)
- [HTTP レスポンスステータスコード](/ja/docs/Web/HTTP/Status)
- {{HTTPStatus("308", "308 Permanent Redirect")}}: `301` と同等ですが、リクエストメソッドが変更されません
- {{HTTPStatus("302", "302 Found")}}: 一時リダイレクト
