---
title: CanvasRenderingContext2D.canvas
slug: Web/API/CanvasRenderingContext2D/canvas
translation_of: Web/API/CanvasRenderingContext2D/canvas
---
<div>{{APIRef}}</div>

<p><a href="/ja/docs/Web/API/Canvas_API">Canvas API</a> の一部である<code><strong>CanvasRenderingContext2D.canvas</strong></code> プロパティは、context に関連づけられた {{domxref("HTMLCanvasElement")}}  オブジェクトへの読み込み専用の参照です。 {{HTMLElement("canvas")}} に関連づけられていない場合は {{jsxref("null")}} になることがあります。</p>

<h2 id="構文">構文</h2>

<pre class="syntaxbox"><var><em>ctx</em></var>.canvas;</pre>

<h2 id="例">例</h2>

<p>以下の例は HTML ドキュメントに次の {{HTMLElement("canvas")}} 要素があるものとしています:</p>

<pre class="brush: html">&lt;canvas id="canvas"&gt;&lt;/canvas&gt;
</pre>

<p><code>CanvasRenderingContext2D</code> の中にある canvas 要素への参照を <code>canvas</code> プロパティから取得できます:</p>

<pre class="brush: js">var canvas = document.getElementById('canvas');
var ctx = canvas.getContext('2d');
ctx.canvas // HTMLCanvasElement
</pre>

<h2 id="仕様">仕様</h2>

<table class="standard-table">
 <tbody>
  <tr>
   <th scope="col">Specification</th>
   <th scope="col">Status</th>
   <th scope="col">Comment</th>
  </tr>
  <tr>
   <td>{{SpecName('HTML WHATWG', "scripting.html#dom-context-2d-canvas", "CanvasRenderingContext2D.canvas")}}</td>
   <td>{{Spec2('HTML WHATWG')}}</td>
   <td></td>
  </tr>
 </tbody>
</table>

<h2 id="ブラウザ互換性">ブラウザ互換性</h2>



<p>{{Compat("api.CanvasRenderingContext2D.canvas")}}</p>

<h2 id="参考情報">参考情報</h2>

<ul>
 <li>{{domxref("CanvasRenderingContext2D")}} インターフェース</li>
 <li><a href="/ja/docs/Web/API/Canvas_API">Canvas API</a></li>
</ul>
