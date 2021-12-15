---
title: CSS Containment
slug: Web/CSS/CSS_Containment
translation_of: Web/CSS/CSS_Containment
---
<p>{{CSSRef}}<br>
 CSS Containment という仕様の目的は、開発者に Web ページの任意のサブツリーをそれ以外から独立させることでサイトパフォーマンスを向上させることです。もしブラウザがページの一部が独立していることを知っていれば、レンダリング時に最適化し、パフォーマンスを向上させることができます。この仕様は単一の CSS プロパティ {{cssxref("contain")}} を定義しています。この文書ではその仕様の基本的な目的を説明しています。</p>

<h2 id="基本例">基本例</h2>

<p>多くの Web ページでは、互いに独立したいくつかのセクションで構成されています。例えば記事の見出しと内容が並んだ以下のようなマークアップで紹介します。</p>

<pre class="brush: html notranslate">&lt;h1&gt;My blog&lt;/h1&gt;
&lt;article&gt;
  &lt;h2&gt;Heading of a nice article&lt;/h2&gt;
  &lt;p&gt;Content here.&lt;/p&gt;
&lt;/article&gt;
&lt;article&gt;
  &lt;h2&gt;Another heading of another article&lt;/h2&gt;
  &lt;p&gt;More content here.&lt;/p&gt;
&lt;/article&gt;</pre>

<p>各 <code>&lt;article&gt;</code> の CSS には {{cssxref("contain")}} プロパティに <code>content</code> という値が設定されています。</p>

<pre class="brush: css notranslate">article {
  contain: content;
}</pre>

<p>各 <code>&lt;article&gt;</code> は他の article タグとは独立しており、 この時 <code>contain: content</code> はブラウザにそのことを伝えるために設定されています。ブラウザは次にこの情報をコンテンツのレンダリング方法の決定に用います。例えば、表示可能な領域の外側の記事はレンダリングしない場合があります。</p>

<p>各 <code>&lt;article&gt;</code> に <code>contain</code> プロパティが与えられた場合、新しい要素が追加されると、ブラウザは <code>contain</code> プロパティが設定された要素のサブツリーの外側については再レイアウトや再描画を行う必要がないと判断します。ただし、もし <code>&lt;article&gt;</code> が ( <code>height: auto</code> が設定されている時のように) そのコンテンツによってサイズが変わるようスタイリングされている場合は、ブラウザがサイズの変化に対応する必要があるかもしれません。</p>

<p><code>contain</code> プロパティについて、各 <code>&lt;article&gt;</code> の要素が独立である例を用いて説明しました。</p>

<p>この <code>content</code> という値は <code>contain: layout paint</code> の省略記法です。ブラウザに対して、内部で行われるレイアウト時にその他の要素と完全に区別するよう伝え、要素に関する全てがその境界の内側で描画されます。どの要素も視覚的にオーバーフローしません。</p>

<p>ある要素のスタイルがその外側に影響しないようにすべきということは、web 開発者側にとってはよく知られており、実際ページを作るときにはそうします。しかし、ブラウザはそういった意図は分かりませんし、記事のスタイルがその中で閉じるように描画されるということは最初から分かりません。このプロパティはそのことをブラウザに伝えるのに有用なのです。これを使うことで、こうした知見に基づいたパフォーマンス最適化を行うことができます。</p>

<h2 id="主な概念と用語">主な概念と用語</h2>

<p>この仕様は {{cssxref("contain")}} というプロパティのみを定義しています。このプロパティの値には、封じ込めの種類を指定します。</p>

<h3 id="レイアウトの封じ込め">レイアウトの封じ込め</h3>

<pre class="brush: css notranslate">article {
  contain: layout;
}</pre>

<p>レイアウトは通常、ドキュメント全体がスコープになっています。つまり、ドキュメント全体の中からたった１つの要素を動かしただけで、様々なところが動かされたかのように扱われます。<code>contain: layout</code> を使うことで、ブラウザに対して必要な要素のみを伝えることができます。このプロパティを指定した要素の中の全てがその要素によって封じ込められ、その他の要素には影響せず、そしてその包含ブロックは独立したフォーマッティングコンテキストになります。</p>

<p>加えて、以下の点に注意する必要があります。</p>

<ul>
 <li><code>float</code> レイアウトはこのプロパティとは独立して作用します。</li>
 <li>マージンはレイアウトによる封じ込めの境界によって崩れることはありません。</li>
 <li>レイアウトの封じ込めは <code>position: </code><code>absolute</code>/<code>fixed</code> が指定されたブロックの子孫要素の包含ブロックになります。</li>
 <li>この包含ブロックはスタッキングコンテキストを作ります。なので {{cssxref("z-index")}} を使うことができます。</li>
</ul>

<h3 id="ペイントの封じ込め">ペイントの封じ込め</h3>

<pre class="brush: css notranslate">article {
  contain: paint;
}</pre>

<p>Paint containment essentially clips the box to the padding edge of the principal box. There can be no visible overflow. The same things are true for <code>paint</code> containment as <code>layout</code> containment (see above).</p>

<p>Another advantage is that if the containing box is offscreen, the browser does not need to paint its contained elements — these must also be offscreen as they are contained completely by that box.</p>

<h3 id="サイズの封じ込め">サイズの封じ込め</h3>

<pre class="brush: css notranslate">article {
  contain: size;
}</pre>

<p>Size containment does not offer much in the way of performance optimizations when used on its own. However, it means that the size of the element's children cannot affect the size of the element itself — its size is computed as if it had no children.</p>

<p>If you turn on <code>contain: size</code> you need to also specify the size of the element you have applied this to. It will end up being zero-sized in most cases, if you don't manually give it a size.</p>

<h3 id="スタイルの封じ込め">スタイルの封じ込め</h3>

<pre class="brush: css notranslate">article {
  contain: style;
}</pre>

<p>Despite the name, style containment does not provide scoped styles such as you would get with the <a href="/ja/docs/Web/Web_Components/Using_shadow_DOM">Shadow DOM</a>. The main use case is to prevent situations where a <a href="/ja/docs/Web/CSS/CSS_Counter_Styles/Using_CSS_counters">CSS Counter</a> could be changed in an element, which could then affect the rest of the tree. </p>

<p>Using <code>contain: style</code> would ensure that the {{cssxref("counter-increment")}} and {{cssxref("counter-set")}} properties created new counters scoped to that subtree only.</p>

<div class="blockIndicator note">
<p><strong>Note</strong>: <code>style</code> containment is "at-risk" in the spec and may not be supported everywhere (it's not currently supported in Firefox).</p>
</div>

<h3 id="特殊な値">特殊な値</h3>

<p>There are two special values of contain:</p>

<ul>
 <li><code>content</code></li>
 <li><code>strict</code></li>
</ul>

<p>We encountered the first in the example above. Using <code>contain: content</code> turns on <code>layout</code> and <code>paint</code> containment. The specification describes this value as being "reasonably safe to apply widely". It does not apply <code>size</code> containment, so you would not be at risk of a box ending up zero-sized due to a reliance on the size of its children.</p>

<p>To gain as much containment as possible use <code>contain: strict</code>, which behaves the same as <code>contain: size layout paint</code>, or perhaps the following to also add <code>style</code> containment in browsers that support it:</p>

<pre class="brush: css notranslate">contain: strict;
contain: strict style;</pre>

<h2 id="参考リンク">参考リンク</h2>

<h3 id="CSS_プロパティ">CSS プロパティ</h3>

<ul>
 <li>{{cssxref("contain")}}</li>
</ul>

<h2 id="外部リンク">外部リンク</h2>

<ul>
 <li><a href="https://blogs.igalia.com/mrego/2019/01/11/an-introduction-to-css-containment/">An Introduction to CSS Containment</a></li>
</ul>
