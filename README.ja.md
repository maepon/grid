##Grid

A simple guide to responsive design.<br>
www.adamkaplan.me/grid

レスポンシブデザイン入門<br>
www.adamkaplan.me/grid

####Why bother with responsive?
We want our websites to be useable on all devices by responding to the user’s behavior, screen size and screen orientation.

####なぜ、レスポンシブに労力を費やすのか?
私達は全てのデバイスにおいて、スクリーンのサイズや縦横の方向といったユーザーの環境に合わせて、ウェブサイトが利用しやすくなることを望んでいます。

####A Fragmented World
As of 2013, there are thousands of different devices and screen sizes that browse the internet, so it's impossible to design layouts to target them all. Instead, we must take a more fluid approach to design.

####断片化された世界
2013年現在、数千種類のデバイスとスクリーンサイズがインターネットにアクセスしています。それら全てに対して、それぞれレイアウトを設計するのはもはや不可能です。そんなことより、デザインにより流動的なアプローチを取り入れるべきでしょう。

####Mobile First
The term “mobile first” gets thrown around a lot lately. What it really means is to start with mobile styles and layer on styles optimized for larger screens only as needed. In other words, your mobile styles become the default and you no longer have to override them later. It’s much simpler!

####モバイルファースト
最近になって「モバイルファースト」という言葉がそこらじゅうで聞かれるようになりました。その言葉は、モバイル向けのスタイルから始めて、必要とされる時に大きなスクリーンに最適化したスタイルを適用するということを意味します。言い換えると、作成したモバイル向けのスタイルがデフォルトになり、それ以降に書き換える必要はないということです。それもうはるかにシンプルです！

> By assuming a flexible but simple layout by default, you can better guard against browsers—with viewports wide and small—that aren’t quite capable of the full responsive layout. So when we’re talking about layout, “mobile first” really means “progressive enhancement.” —Ethan Marcotte


> デフォルトでは柔軟でシンプルなレイアウトを想定することで、ビューポートが広いブラウザや、狭くてレスポンシブウェブデザインに対応できないブラウザにもより良い対応ができます。そういう意味で、私達がレイアウトについて話すときには、「モバイルファースト」の真意は「プログレッシブエンハンスメント」であると言っています。（Ethan Marcotte）

##Min-width Media Queries
Introduce layout-specific rules only when you need them. Use `min-width` to layer complexity on your layout as the viewport widens. It’s easier to have all the media queries nearby, rather than at the end of the stylesheet or in a separate document.

##min-widthメディアクエリー
必要な場合のみレイアウトに固有なルールを導入します。レイアウトがビューポートが広がるにつれて複雑になっていくように`min-width`を利用します。全てのメディアクエリーはスタイルシートの最後や別ファイルにしてしまうよりは、対象の記述の近くに存在するほうがやりやすいでしょう。


```css
/* Small screens (default) */
html { font-size: 100%; }

/* Medium screens (640px) */
@media (min-width: 40rem) {
  html { font-size: 112%; }
}

/* Large screens (1024px) */
@media (min-width: 64rem) {
  html { font-size: 120%; }
}
```

##Steps

##手順

####1. Not All Browsers are Created Equal
Browsers will render your CSS differently. To avoid this, it’s a good idea to use a modern alternative to a reset like [Normalize.css](http://necolas.github.io/normalize.css/), which will render elements more consistently cross-browser. Remember to include it as-is before your stylesheet.

####1. 全てのブラウザは同じように作られていない
ブラウザたちはCSSを同じようにレンダリングしないでしょう。これを回避するためには、リセットの現代的な代替手段である[Normalize.css](http://necolas.github.io/normalize.css/)といったものを利用することをおすすめします。より一貫性のあるクロスブラウザへの対応でレンダリングされるでしょう。あなたのスタイルシートの前に読み込むことを忘れないで下さい。

```html
<link rel="stylesheet" href="/css/normalize.css">
<link rel="stylesheet" href="/css/grid.css">
```

####2. Add the Viewport Meta Tag
Place in the `<head>` of your HTML. This enables use of media queries for cross-device layouts.

####2. metaタグにviewportを追加する
HTMLの`<head>`内に配置します。これにより、様々なデバイスでレイアウトできるようになります。

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

##CSS Box Model
It’s important to understand the basics, like how elements are generated and behave in the browser, before diving into responsive web design. The CSS Box Model consists of four distinct parts.

##CSSボックスモデル
CSSボックスモデルへの理解は、レスポンシブ・ウェブ・デザインに飛び込む前に、各要素がブラウザの中でどのように生成されふるまうかといった基本として重要です。CSSボックスモデルは4つの要素から構成されています。

###Content
The content of the box, where text and images appear.

###Padding
Clears an area around the content.

###Border
A border that goes around the padding.

###Margin
Clears an area around the border.

####3. Use box-sizing: border-box
Place at the top of your CSS file. The `*` will target all elements on the page.

####3. box-sizing: border-boxを利用する
CSSファイルの先頭に記述しします。 `*` はページ内の全ての要素を指します。

```css
*, *:before, *:after {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}
```
##Your Choice
[What was once a bug](http://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug) is now a widely used CSS property. It basically means you can choose whether or not to include borders and padding in the width of your content.

このかつてのバグは今や広く用いられるCSSのプロパティとなりました。これは、コンテンツの幅を決めるときにボーダーとパディングを含めるのか否かをあなたが選択できることを意味しています。

###Without box-sizing: border-box
Margin, borders and padding are drawn outside the set width of your content.

###box-sizing: border-box なし
マージン、ボーダー、パディングは内容の幅の外側に描画されます。

###With box-sizing: border-box
Borders and padding are drawn inside the set width of your content. The margin is drawn outside.

###box-sizing: border-box あり
ボーダーとパディングは内容の幅の中に描画されます。マージンは外側に描画されます。

####4. Create a Container
A container holds all elements and controls the page's maximum width. Using a container will make designing for responsive easier!

####4. コンテナーを作成する
コンテナーは、全ての要素を保持し、ページの最大幅に収めます。コンテナーを利用すればレスポンシブなデザインは簡単になります！

```css
.container {
  margin: 0 auto;
  max-width: 48rem;
  width: 90%;
}
```

```html
<div class="container">
  <!-- Your Content -->
</div>
```

####5. Create a Column
With mobile first, columns are `block` level (takes up the full width available) by default. No additional styles needed!

####5. カラムを作成する
モバイルファーストでは、基本的にカラムは`ブロック`レベル（利用可能な幅を全て含む）になります。追加のスタイルはいりません！

```html
<div class="container">
  <div class="column">
    <!-- Your Content -->
  </div>
</div>
```

####6. Create Column Sizes
On larger screens, columns gain `float: left` in order to stack content horizontally. Columns now use padding for gutters, so you no longer need to worry about removing margins.

####6. カラムのサイズを設定する

大きなスクリーンでは、カラムにコンテンツを水平方向に配置する目的で `float: left` を設定します。カラムの間隔にはパディングを利用するので、マージンの除去を心配する必要はありません。

```html
<div class="container">
  <div class="row">
    <div class="column half">
      <!-- Your Content -->
    </div>
    <div class="column half">
      <!-- Your Content -->
    </div>
  </div>
</div>
```

```css
@media (min-width: 40rem) {
  .column {
    float: left;
    padding-left: 1rem;
    padding-right: 1rem;
  }

  .column.full { width: 100%; }
  .column.two-thirds { width: 66.7%; }
  .column.half { width: 50%; }
  .column.third { width: 33.3%; }
  .column.fourth { width: 25%; }
  .column.flow-opposite { float: right; }
}
```

####7. Create Rows
Columns are wrapped in rows to prevent other elements from stacking next to them, otherwise know as clearing issues. Rows are cleared using the popular `clearfix`, which was created by [Nicolas Gallagher](http://nicolasgallagher.com/micro-clearfix-hack/).

####7. 行の作成
カラムは他の要素に続いて配置されることを防ぐ目的で、行ごとにラッピングされます。でないと、配置の解除に問題が発生することが知られています。行は[Nicolas Gallagher](http://nicolasgallagher.com/micro-clearfix-hack/)が作成した `clearfix` で配置の解除を行うことが一般的です。

```html
<div class="container">
  <div class="row clearfix">
    <div class="column half">
      <!-- Your Content -->
    </div>
    <div class="column half">
      <!-- Your Content -->
    </div>
  </div>

  <div class="row clearfix">
    <div class="column half">
      <!-- Your Content -->
    </div>
    <div class="column half">
      <!-- Your Content -->
    </div>
  </div>
</div>
```

```css
.clearfix:before,
.clearfix:after {
  content: " ";
  display: table;
}

.clearfix:after {
  clear: both;
}

.clearfix {
  *zoom: 1;
}
```

#### Flow Opposite
Add the class `.flow-opposite` to columns where you want content to display first on mobile but appear on the right on larger screens.

#### 反対側へ流す(Flow Opposite)

モバイルではいち早く表示しつつ、大きなスクリーンでは右に配置したいコンテンツには、`.flow-opposite`クラスを付与します。

```html
<div class="container">
  <div class="row clearfix">
    <div class="column half flow-opposite">
      <!-- Your Content -->
    </div>
    <div class="column half">
      <!-- Your Content -->
    </div>
  </div>
</div>
```

```css
@media (min-width: 40rem) {
  .column.flow-opposite { float: right; }
}
```

##Practice Makes Perfect
By following these simple steps, you are on the path to responsive web design mastery. Keep practicing and help make the web a better, more useable place.

##勉強はおわりました
この手順を踏むことで、あなたはレスポンシブ・ウェブ・デザインを修得する過程に踏み込みました。このまま勉強を続けてウェブをより良く、より利用しやすい場にすることに参加してください。

####Further Reading

####参考文献

* [A Book Apart: Mobile First](http://www.abookapart.com/products/mobile-first)
* [A Book Apart: Responsive Web Design](http://www.abookapart.com/products/responsive-web-design)
* [Beginner’s Guide to Responsive Web Design](http://blog.teamtreehouse.com/beginners-guide-to-responsive-web-design)
* [Box-sizing: Border-box FTW](http://www.paulirish.com/2012/box-sizing-border-box-ftw/)
* [Don't Forget the Viewport Meta Tag](http://dev.tutsplus.com/articles/quick-tip-dont-forget-the-viewport-meta-tag--webdesign-5972)
* [The Many Faces of ‘Mobile First’](http://bradfrostweb.com/blog/mobile/the-many-faces-of-mobile-first/)
* [Understanding the Humble Clearfix](http://fuseinteractive.ca/blog/understanding-humble-clearfix)

####References

####参考資料

* [Android Fragmentation Visualized](http://opensignal.com/reports/fragmentation-2013/)
* [Animate.css](http://daneden.github.io/animate.css/)
* [Box Model](http://developer.mozilla.org/en-US/docs/Web/CSS/box_model)
* [Chrome Developer Tools](http://developers.google.com/chrome-developer-tools/)
* [Code samples by GitHub Gist](https://gist.github.com/aekaplan)
* [Internet Explorer Box Model](http://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug)
* [Progressive Enhancement](http://coding.smashingmagazine.com/2009/04/22/progressive-enhancement-what-it-is-and-how-to-use-it/)
