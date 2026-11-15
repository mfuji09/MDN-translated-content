---
title: import.meta.resolve()
slug: Web/JavaScript/Reference/Operators/import.meta/resolve
l10n:
  sourceCommit: 696a0436bb4dd20eb4d30ac3f1d4fc5140d1eee9
---

**`import.meta.resolve()`** は JavaScript モジュールの [`import.meta`](/ja/docs/Web/JavaScript/Reference/Operators/import.meta) オブジェクトで定義されている組み込み関数で、現在のモジュールの URL をベースとしてモジュール指定子を URL に解決します。

## 構文

```js-nolint
import.meta.resolve(moduleName)
```

### 引数

- `moduleName`
  - : インポート可能なモジュールを指定する文字列。これは相対パス（`"./lib/helper.js"` など）、ベア名（`"my-module"` など）、絶対 URL（`"https://example.com/lib/helper.js"` など）のいずれかです。

### 返値

引数が [`import()`](/ja/docs/Web/JavaScript/Reference/Operators/import) に渡された場合にインポートされるパスに対応する文字列を返します。

## 解説

`import.meta.resolve()` により、スクリプトは次のように名前に対するモジュール指定子の解決アルゴリズムにアクセスできます。

```js
// -- https://example.com/main.js --

const helperPath = import.meta.resolve("./lib/helper.js");
console.log(helperPath); // "https://example.com/lib/helper.js"
```

`import.meta.resolve()` はモジュール指定子の解決だけを行い、結果のモジュールを[読み込んだり](/ja/docs/Web/JavaScript/Guide/Modules/Module_graph#グラフの読み込み)、インポートしたりはしません。ブラウザーでは、返された URL が実在するファイルに対応するか、そのファイルにモジュールとして有効なコードが含まれるかにかかわらず、返値は同じです。この操作は同期的です。ブラウザー以外のホストでは、解決中にファイルシステムを調べることがあります。たとえば Node.js は、パッケージのメタデータを読み込んだり、パスを確認したりできます。

これは[動的インポート](/ja/docs/Web/JavaScript/Reference/Operators/import)とは異なります。どちらも第一引数としてモジュール指定子を受け取りますが、 `import.meta.resolve()` はそのパスにアクセスしようとすることなく、インポートされるであろうパスを返します。したがって、次の 2 つは実質的に同じコードです。

```js
// アプローチ 1
console.log(await import("./lib/helper.js"));

// アプローチ 2
const helperPath = import.meta.resolve("./lib/helper.js");
console.log(await import(helperPath));
```

しかし、 `"./lib/helper.js"` が正常にインポートできなくても、 2 行目のスニペットがインポートを実行するまでエラーは発生しません。

### ベアモジュール名

その名前に対してモジュール解決が定義されていれば、 `import.meta.resolve()` に素のモジュール名（素のモジュール指定子としても知られています）を渡すことができます。例えば、ブラウザー内で[インポートマップ](/ja/docs/Web/JavaScript/Guide/Modules/Modules_on_the_web#インポートマップを使用したモジュールのインポート)を使って定義できます。

```html
<!-- index.html -->
<script type="importmap">
  {
    "imports": {
      "my-module": "./modules/my-module/index.js"
    }
  }
</script>

<script type="module">
  const moduleEntryPath = import.meta.resolve("my-module");
  console.log(moduleEntryPath);
</script>
```

繰り返しますが、この例では `moduleEntryPath` をインポートせず、インポートマップもそれ自体ではモジュールをインポートしません。そのため、対象のファイルが実際に存在するかどうかにかかわらず、解決された URL が表示されます。

### new URL() との比較

[`URL()`](/ja/docs/Web/API/URL/URL) コンストラクターは第二引数としてベース URL を受け付けます。第一引数が相対パスで、ベース URL が [`import.meta.url`](/ja/docs/Web/JavaScript/Reference/Operators/import.meta#値) の場合、 `import.meta.resolve()` と同様の効果があります。

```js
const helperPath = new URL("./lib/helper.js", import.meta.url).href;
console.log(helperPath);
```

これは、古いブラウザーをターゲットにする場合にも便利な置換構文です。ただし、いくつかの違いがあります。

- `import.meta.resolve()` は文字列を返し、 `new URL()` は `URL` オブジェクトを返します。構築された `URL` に対して [`href`](/ja/docs/Web/API/URL/href) や [`toString()`](/ja/docs/Web/API/URL/toString) を使用することも可能ですが、 JavaScript の環境によっては、あるいはバンドラーのようなツールを使用してコードを静的に解析する場合には、まったく同じ結果にならないことがあります。
- `import.meta.resolve()` は、上で説明したように、インポートマップを使用したベアモジュール名の解決など、追加の解決設定を認識します。新しい `URL()` はインポートマップを意識せず、ベアモジュール名を相対パスとして扱います（つまり、 `new URL("my-module", import.meta.url)` は `new URL("./my-module", import.meta.url)` を意味します）。

いくつかのツールは `new URL("./lib/helper.js", import.meta.url).href` を `"./lib/helper.js"` への依存関係（インポートに似ている）として認識し、バンドル、移動したファイルのインポートの書き換え、"go to source" 機能などの機能のためにこれを考慮します。しかし、 `import.meta.resolve()` は曖昧さが少なく、特にモジュールパスの解決依存を示すように設計されているため、これらの使用例では可能な限り `import.meta.resolve(moduleName)` を `new URL(moduleName, import.meta.url)` の代わりに使用する必要があります。

### ECMAScript の機能ではない

`import.meta.resolve()` は JavaScript モジュールの [ECMAScript 仕様書](/ja/docs/Web/JavaScript/Reference/JavaScript_technologies_overview#javascript_コア言語_ecmascript)の一部として定義も文書化もされていません。その代わりに、ECMAScript 仕様書は [`import.meta` オブジェクト](https://tc39.es/ecma262/multipage/ecmascript-language-expressions.html#prod-ImportMeta)<sup>(英語)</sup>を定義していますが、[そのすべてのプロパティを「ホスト定義」のままにしています](https://tc39.es/ecma262/multipage/ecmascript-language-expressions.html#sec-hostgetimportmetaproperties)<sup>(英語)</sup>。WHATWG HTML 標準は ECMAScript 標準が規定していない部分を補い、[モジュール指定子の解決](https://html.spec.whatwg.org/multipage/webappapis.html#resolve-a-module-specifier)<sup>(英語)</sup>を使って [`import.meta.resolve` を定義しています](https://html.spec.whatwg.org/multipage/webappapis.html#hostgetimportmetaproperties)<sup>(英語)</sup>。

つまり、 `import.meta.resolve()` はすべての適合する JavaScript 実装で実装される必要はありません。しかし、 `import.meta.resolve()` はブラウザー以外の環境でも利用できるかもしれません：

- Deno は[ブラウザーの動作との互換性](https://docs.deno.com/api/node/module/#ImportMeta.methods)<sup>(英語)</sup>を実装しています。
- Node.js も [`import.meta.resolve()` 関数](https://nodejs.org/docs/latest/api/esm.html#importmetaresolvespecifier)<sup>(英語)</sup>を実装していますが、`--experimental-import-meta-resolve` フラグを使用すると、追加の `parent` 引数を指定できます。

## 例

### Worker() コンストラクターのパスを解決

`import.meta.resolve()` は、 [`Worker()`](/ja/docs/Web/API/Worker/Worker) コンストラクターのように、スクリプトファイルへのパスを引数として受け取る API で特に有用です。

```js
// -- main.js --
const workerPath = import.meta.resolve("./worker.js");
const worker = new Worker(workerPath, { type: "module" });
worker.addEventListener("message", console.log);
```

```js
// -- worker.js --
self.postMessage("hello!");
```

これは、[サービスワーカー](/ja/docs/Web/API/ServiceWorker) や [共有ワーカー](/ja/docs/Web/API/SharedWorker) など、他のワーカーのパスを計算するのにも便利です。ただし、相対パスを使用してサービスワーカーの URL を計算する場合、既定では解決されたパスのディレクトリーが[登録スコープ](/ja/docs/Web/API/ServiceWorkerRegistration/scope)を決定することに注意してください（ただし、[登録時](/ja/docs/Web/API/ServiceWorkerContainer/register)に別のスコープを指定することもできます）。

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [`import`](/ja/docs/Web/JavaScript/Reference/Statements/import)
- [`import()`](/ja/docs/Web/JavaScript/Reference/Operators/import)
- [`import.meta`](/ja/docs/Web/JavaScript/Reference/Operators/import.meta)
