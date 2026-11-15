---
title: import.meta
slug: Web/JavaScript/Reference/Operators/import.meta
l10n:
  sourceCommit: 696a0436bb4dd20eb4d30ac3f1d4fc5140d1eee9
---

**`import.meta`** オブジェクトはコンテキスト固有のメタデータを JavaScript のモジュールに公開します。これには、モジュールの URL のようなモジュールに関する情報が含まれています。

## 構文

```js-nolint
import.meta
```

### 値

`import.meta` オブジェクトはホスト環境によって生成され、拡張可能な [`null` プロトタイプ](/ja/docs/Web/JavaScript/Reference/Global_Objects/Object#null_プロトタイプオブジェクト)オブジェクトとして、すべてのプロパティが書き込み可能、構成可能、列挙可能となります。仕様では定義すべきプロパティは指定されていませんが、ホストは通常次のプロパティを実装します。

- `url`
  - : モジュールの完全な URL。クエリー引数やハッシュ（`?` または `#` の後に続く部分）を含みます。ブラウザーでは、外部スクリプトの場合はスクリプトを取得した URL、インラインスクリプトの場合はモジュールスクリプトの作成時点での文書のベース URL です。Node.js では、ファイルベースのモジュールには `file:` URL が、その他の対応する URL スキームから読み込まれたモジュールにはそれぞれの URL が使用されます。
- [`resolve`](/ja/docs/Web/JavaScript/Reference/Operators/import.meta/resolve)
  - : 現在のモジュールの URL を基点として、モジュール指定子を URL に解決します。

## 解説

`import.meta` 構文は、キーワード `import`、ドット、識別子 `meta` で構成されます。 `import` は識別子ではなく[予約語](/ja/docs/Web/JavaScript/Reference/Lexical_grammar#予約語)であるため、これは[プロパティアクセサー](/ja/docs/Web/JavaScript/Reference/Operators/Property_accessors)ではなく、特別な式構文です。

`import.meta` メタプロパティは JavaScript モジュール内で利用できます。モジュール外（モジュール内での[直接 `eval()`](/ja/docs/Web/JavaScript/Reference/Global_Objects/eval#直接的または間接的な_eval) も含む）で `import.meta` を使用すると構文エラーになります。

## 例

### クエリー引数を渡す

`import` 指定子でクエリー引数を指定すると、モジュール固有の引数を渡せます。これは、アプリケーション全体の [`window.location`](/ja/docs/Web/API/Window/location)（Node.js では `process.argv` 経由）から引数を取得する手法を補完します。例えば、次の HTML では、

```html
<script type="module">
  import "./index.mjs?someURLInfo=5";
</script>
```

`index.mjs` モジュールは、`import.meta` を通じて `someURLInfo` 引数を取得できます。

```js
// -- index.mjs --
new URL(import.meta.url).searchParams.get("someURLInfo"); // 5
```

ファイルが別のファイルをインポートする場合も同様です。

```js
// -- index.mjs --
import "./index2.mjs?someURLInfo=5";

// -- index2.mjs --
new URL(import.meta.url).searchParams.get("someURLInfo"); // 5
```

Node.js の ES モジュール実装は、後者の例のようにクエリー引数（またはハッシュ）を含むモジュール指定子の解決に対応しています。ただし、CLI コマンド（例えば `node index.mjs?someURLInfo=5`）でモジュールを指定する場合、クエリーやハッシュは使用できません。CLI のエントリーポイントは CommonJS に似た解決モードを採用しており、パスを URL ではなくファイルパスとして扱うためです。エントリーポイントモジュールに引数を渡すには、CLI 引数を使用し、`process.argv` を通じて読み取ってください（例: `node index.mjs --someURLInfo=5`）。

### 現在のファイルからの相対パスによるファイルの解決

Node.js の CommonJS モジュールには、現在のモジュールを含むフォルダーの絶対パスを保持する `__dirname` 変数があり、相対パスの解決に役立ちます。ただし、Node.js は ES モジュールではこの変数を提供しません。相対ファイルを解決するには `import.meta.url` を使用できます。この方法では、ファイルシステムのパスではなく URL を使用します。

使用前 (CommonJS):

```js
const fs = require("fs/promises");
const path = require("path");

const filePath = path.join(__dirname, "someFile.txt");
fs.readFile(filePath, "utf8").then(console.log);
```

使用後 (ES モジュール):

```js
import fs from "node:fs/promises";

const fileURL = new URL("./someFile.txt", import.meta.url);
fs.readFile(fileURL, "utf8").then(console.log);
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- {{jsxref("Statements/import", "import")}}
- {{jsxref("Statements/export", "export")}}
