[[HOME]]

**D3.js** は document ベースでデータを操作するための JavaScript ライブラリです。 **D3** を使うことで、 THML, SVG, CSS を利用し、データを表現する事ができます。 D3 が web 標準を強調している理由は、プロプライエタリなフレームワークを使うことなしに、パワフルな視覚化要素と DOM 操作でのデータ駆動アプローチを結びつけ、モダンブラウザで十分に実施することができることです。

## Resources

* [はじめに](http://mbostock.github.com/d3/)
* [[事例ギャラリー|Gallery]]
* [[チュートリアル|Tutorials]]
* [[API Reference]]
* [[Release Notes]]
* [d3.js on Stack Overflow](http://stackoverflow.com/questions/tagged/d3.js)
* [d3-js Google Group](http://groups.google.com/group/d3-js)

## ブラウザサポート

D3 は、いわゆる "モダン" ブラウザ (一般的に、IE8およびそれ以前を除くすべて) をサポートします。 D3 は、 Firefox, Chrome (Chromium), Safari (Webkit), Opera および IE9 に対してテストされています。 D3 ライブラリのコア, JavaScript と [W3C DOM](http://www.w3.org/DOM/) APIのような最小要求のような D3 の一部は古いブラウザでも機能します。 IE8 に対しては、 [Aight](https://github.com/shawnbot/aight) という互換ライブラリが推奨されています。 D3 は Level 1 の [Selectors API](http://www.w3.org/TR/selectors-api/) を利用しています。互換性のために [Sizzle](http://sizzlejs.com/) をプリロードしておくことができます。 [SVG](http://www.w3.org/TR/SVG/) と [CSS3 Transitions](http://www.w3.org/TR/css3-transitions/) を利用するためにモダンブラウザが必要となるでしょう。D3 は互換レイヤではないので、ご利用のブラウザが標準をサポートしないのであれば、残念だけど、ごめんね！

## インストール

最新の D3 のはこちらです。

* <http://d3js.org/d3.v3.zip>

最新リリースの直リンクであれば、以下のスニペットをコピーしてください。

```html
<script src="http://d3js.org/d3.v3.min.js"></script>
```

もし、テストを含むリポジトリ全てが必要であれば

* <https://github.com/mbostock/d3/zipball/master>

コマンドラインでも

```bash
git clone git://github.com/mbostock/d3.git
```

もし、ローカルで開発をするのであれば、ローカルファイルシステム以外へのファイル読み込みに厳しい制限のあるブラウザかもしれません。 **もし (d3.json などのような) [d3.xhr](wiki/Requests) をローカルで利用するのであれば、ローカルWebサーバを起動しなければなりません。** 例えば、Pythonでサーバを立てるのであれば：

    python -m SimpleHTTPServer 8888 &

これを動かしたら、 <http://localhost:8888/examples/> を開いてください。

D3 を利用した新しい視覚化を作りたくなったら、 D3 リポジトリから取得すべきです。または、 D3 に新しい機能の追加、バグの修正、テストの実行などで D3 を拡張したい時には、 [D3 リポジトリを fork](/mbostock/d3/fork_select)し、新しいものをインストールするべきです。 D3 のテストフレームワークは [Vows](http://vowsjs.org) で、これは [Node.js](http:/nodejs.org/) と [NPM](http://npmjs.org) を必要とします。もし、あなたの環境が Mac OS X であるならば、 Node も NPM も [Homebrew](http://mxcl.github.com/homebrew/) で簡単にインストールすることができます。

D3 を利用した新しい視覚化を作りたくなったら、 D3 リポジトリから取得すべきです。そうでなく、新しい機能の追加や、バグの修正、テストの実行などで D3 を拡張したいときには、 [D3 リポジトリを fork](/mbostock/d3/fork_select)し、 [Node.js](http://nodejs.org/) をインストールするべきです。このリポジトリのルートから、 D3 の依存関係をインストールすることができます。

    npm install

テストを実施するためには下記のコマンドを入力します。

    make test