---
title: contain
slug: Web/CSS/contain
tags:
  - CSS
  - CSS Containment
  - CSS Property
  - Layout
  - NeedsExample
  - Paint
  - Reference
  - Style
  - Web
  - 'recipe:css-property'
translation_of: Web/CSS/contain
---
<div>{{CSSRef}}</div>

<p><strong><code>contain</code></strong> は <a href="/ja/docs/Web/CSS">CSS</a> のプロパティで、ある要素とその内容が、できる限り多く、文書ツリーの他の部分から<em>独立している</em>ことを示します。これによってブラウザーがレイアウト、スタイル、描画、寸法、およびその組み合わせの再計算を、ページ全体ではなく DOM の限られた領域に対して行うことで、性能上の明らかな利点をもたらします。</p>

<p>このプロパティはページ上にそれぞれ独立したたくさんのウィジェットがあるときに有益であり、ウィジェットの内部を、ウィジェットの囲みボックスの外側の副作用から守るために使用することができます。</p>

<div class="blockIndicator note">
<p><strong>注:</strong> (<code>paint</code>, <code>strict</code>, <code>content</code> のいずれかの値で) 適用された場合、このプロパティは以下のものを生成します。</p>

<ol>
 <li>新しい<a href="/ja/docs/Web/CSS/Containing_block">包含ブロック</a> (対象は {{cssxref("position")}} プロパティが <code>absolute</code> または <code>fixed</code> の子孫)。</li>
 <li>新しい<a href="/ja/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context">重ね合わせコンテキスト</a>。</li>
 <li>新しい<a href="/ja/docs/Web/Guide/CSS/Block_formatting_context">ブロック整形コンテキスト</a>。</li>
</ol>
</div>

<h2 id="Syntax" name="Syntax">構文</h2>

<pre class="brush: css no-line-numbers notranslate ">/* キーワード値 */
contain: none;
contain: strict;
contain: content;
contain: size;
contain: layout;
contain: style;
contain: paint;

/* 複数のキーワード */
contain: size paint;
contain: size layout paint;

/* グローバル値 */
contain: inherit;
contain: initial;
contain: unset;</pre>

<p><code>contain</code> プロパティは以下のうちの一つで指定します。</p>

<ul>
 <li><code>none</code>, <code>strict</code>, <code>content</code> の何れかのキーワードを単独で使用。</li>
 <li><code>size</code>, <code>layout</code>, <code>style</code>, and <code>paint</code> の各キーワードを1つ以上、任意の順序で使用。</li>
</ul>

<h3 id="Values" name="Values">値</h3>

<dl>
 <dt><code>none</code></dt>
 <dd>その要素が通常通り描画され、抑制を適用しないことを示します。</dd>
 <dt><code>strict</code></dt>
 <dd><code>style</code> を除くすべての抑制規則がその要素に適用されることを示します。これは <code>contain: size layout paint</code> と同等です。</dd>
 <dt><code>content</code></dt>
 <dd><code>size</code> および <code>style</code> 以外の抑制規則がその要素に適用されることを示します。これは <code>contain: layout paint</code> と同等です。</dd>
 <dt><code>size</code></dt>
 <dd>子孫の寸法を確認する必要なく、その要素の寸法を変更できることを示します。</dd>
 <dt><code>layout</code></dt>
 <dd>要素の外側が内部のレイアウトなどに影響しないことを示します。</dd>
 <dt><code>style</code></dt>
 <dd>ある要素とその子孫以外に影響を及ぼす可能性のあるプロパティの場合、その要素が含まれている要素をエスケープしないことを示します。なお、この値は仕様書で「リスクあり」と位置づけられており、どこでも対応しているとは限りません。</dd>
 <dt><code>paint</code></dt>
 <dd>その要素の子孫を、境界の外に表示しないことを示します。包含ボックスが画面外の場合、ブラウザーは中の要素を描画する必要はありません。 — そのボックスに完全に含まれていれば、やはり画面外にあるからです。そして、子孫が包含要素の領域を溢れている場合、子孫は包含要素の境界ボックスで切り取られます。</dd>
</dl>

<h2 id="Formal_definition" name="Formal_definition">公式定義</h2>

<p>{{cssinfo}}</p>

<h2 id="Formal_syntax" name="Formal_syntax">形式文法</h2>

{{csssyntax}}

<h2 id="Examples" name="Examples">例</h2>

<h3 id="Simple_layout" name="Simple_layout">単純なレイアウト</h3>

<p>以下のマークアップは多数のコンテンツを持つ記事からなるものです。</p>

<pre class="brush: html notranslate">&lt;h1&gt;My blog&lt;/h1&gt;
&lt;article&gt;
  &lt;h2&gt;Heading of a nice article&lt;/h2&gt;
  &lt;p&gt;Content here.&lt;/p&gt;
&lt;/article&gt;
&lt;article&gt;
  &lt;h2&gt;Another heading of another article&lt;/h2&gt;
  &lt;img src="graphic.jpg" alt="photo"&gt;
  &lt;p&gt;More content here.&lt;/p&gt;
&lt;/article&gt;</pre>

<p>それぞれの <code>&lt;article&gt;</code> および <code>&lt;img&gt;</code> には境界があり、画像は浮動状態です。</p>

<pre class="brush: css notranslate">img {
  float: left;
  border: 3px solid black;
}

article {
  border: 1px solid black;
}</pre>

<p>{{EmbedLiveSample('Simple_layout', '100%', '300')}}</p>

<h3 id="Float_interference" name="Float_interference">浮動要素の干渉</h3>

<p>1つ目の記事の下部に別の画像を挿入すると、 DOM ツリーの大部分が再レイアウトされたり、再描画されたりする可能性があり、2つ目の記事のレイアウトにも支障をきたしてしまいます。</p>

<pre class="brush: html notranslate">&lt;h1&gt;My blog&lt;/h1&gt;
&lt;article&gt;
  &lt;h2&gt;Heading of a nice article&lt;/h2&gt;
  &lt;p&gt;Content here.&lt;/p&gt;
  &lt;img src="i-just-showed-up.jpg" alt="social"&gt;
&lt;/article&gt;
&lt;article&gt;
  &lt;h2&gt;Another heading of another article&lt;/h2&gt;
  &lt;img src="graphic.jpg" alt="photo"&gt;
  &lt;p&gt;More content here.&lt;/p&gt;
&lt;/article&gt;</pre>

<div class="hidden">
<pre class="brush: css notranslate">img {
  float: left;
  border: 3px solid black;
}

article {
  border: 1px solid black;
}</pre>
</div>

<p>ご覧の通り、浮動要素の動作方法が原因で、最初の画像が2つ目の記事の領域内に掛かってしまっています。</p>

<p>{{EmbedLiveSample('Float_interference', '100%', '300')}}</p>

<h3 id="Fixing_with_contain" name="Fixing_with_contain">contain による修正</h3>

<p>それぞれの <code>article</code> の <code>contain</code> プロパティを <code>content</code> の値を設定することで、新しい要素が挿入されたときに、ブラウザーはそれが含まれる要素のサブツリーの再計算をするだけで、その外側には何もする必要がないことを理解します。</p>

<div class="hidden">
<pre class="brush: html notranslate">&lt;h1&gt;My blog&lt;/h1&gt;
&lt;article&gt;
  &lt;h2&gt;Heading of a nice article&lt;/h2&gt;
  &lt;p&gt;Content here.&lt;/p&gt;
  &lt;img src="i-just-showed-up.jpg" alt="social"&gt;
&lt;/article&gt;
&lt;article&gt;
  &lt;h2&gt;Another heading of another article&lt;/h2&gt;
  &lt;img src="graphic.jpg" alt="photo"&gt;
  &lt;p&gt;More content here.&lt;/p&gt;
&lt;/article&gt;</pre>
</div>

<pre class="brush: css notranslate">img {
  float: left;
  border: 3px solid black;
}

article {
  border: 1px solid black;
  contain: content;
}</pre>

<p>これで、最初の画像が2つ目の記事の下に浮いてくることなく、包含する要素の範囲内に留まることも意味します。</p>

<p>{{EmbedLiveSample('Fixing_with_contain', '100%', '330')}}</p>

<h2 id="Specifications" name="Specifications">仕様書</h2>

<table class="standard-table">
 <thead>
  <tr>
   <th scope="col">仕様書</th>
   <th scope="col">状態</th>
   <th scope="col">備考</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>{{SpecName('CSS Containment')}}</td>
   <td>{{Spec2('CSS Containment')}}</td>
   <td>初回定義</td>
  </tr>
 </tbody>
</table>

<h2 id="Browser_compatibility" name="Browser_compatibility">ブラウザーの互換性</h2>

<p>{{Compat("css.properties.contain")}}</p>

<h2 id="See_also" name="See_also">関連情報</h2>

<ul>
 <li><a href="/ja/docs/Web/CSS/CSS_Containment">CSS 抑制</a></li>
 <li>CSS の {{cssxref("position")}} プロパティ</li>
</ul>
