---
layout: post
title: 記事投稿の仕方
category: Web
tags: [初心者向け, jekyll, git, master]
tagline: ~Jekyll入門~
---

**1. Git(GUIクライアント)をインストールする**

 - **Windowsの場合** [GitHub for Windows](http://windows.github.com/)がオススメです  
 使い方は[github-for-windows-tutorial](http://chocolatina.github.com/github-for-windows-tutorial/)を参考にしましょう
 - **Macの場合** [GitHub for Mac](http://mac.github.com/)がオススメです
 - **Linuxの場合** [Ubuntu Weekly Recipe：第212回　Git/Bazaarブラウザあれこれ｜gihyo.jp … 技術評論社](http://gihyo.jp/admin/serial/01/ubuntu-recipe/0212) を参考にしましょう

**2. リポジトリを取ってくる**

**3. 記事を書く**  
以下のディレクトリ構造は例ですが、

	.
	|-- _posts
	    |-- 20011-10-25-open-source-is-good.md
	    |-- 20011-04-26-hello-world.md

このように\_postsのフォルダ内に`yyyy-mm-dd-title.md`という形で追加していきます。

**yyyy-mm-dd-title.md**

```yaml
---
layout: post
title: タイトル
category: lessons
tags: [beginner, jekyll, tutorial]
tagline: タグライン
---

内容
```

####注意
 - ファイル名に日本語は不可
 - カテゴリに日本語は使えない
 - タグに日本語は使える

.md の例を載せましたが、.html や .textile も使えます。  
.mdとはMarkdownファイルの拡張子です。Markdown記法で書くと、自動でHTMLに変換してくれます。
Markdown記法はとても簡単なので以下のサイトを参考に試してみるといいでしょう。

 - [Showdown - Markdown in Javascript](http://pamgau.net/showdown/)
   (オンラインでMarkdown表記をHTMLに変換してくれて、リアルタイムのプレビューが可能です。)
 - [リアルタイムプレビュー対応の国産“Markdown”エディター「MarkDown#Editor」](http://www.forest.impress.co.jp/docs/review/20120905_557582.html) (Windows用)
 - [リアルタイムプレビューにも対応、“Markdown”専用のエディター「MarkdownPad」](http://www.forest.impress.co.jp/docs/review/20111020_485035.html) (Windows用)
 - [Markdown - Wikipedia](http://ja.wikipedia.org/wiki/Markdown)
 - [Markdown の記法](http://technetium.matrix.jp/markdown.html)
 - [Markdown文法の全訳](http://blog.2310.net/archives/6)

**4. コミットして、pushする(公開する)**

###参考ページ
- [GitHub Pagesホスティングサービス(ほぼ)完全活用ガイド](http://tokkono.cute.coocan.jp/blog/slow/index.php/programming/github-pages-almost-perfect-guide/) 
- [脱GitHub初心者を目指す人のREADMEマークダウン使いこなし術](http://tokkono.cute.coocan.jp/blog/slow/index.php/programming/markdown-skills-for-github-beginners/) 
- [サイト編集の仕方](https://github.com/moto-net/moto-net.github.com/wiki/Edit-Site) (ローカルでの確認方法)
- [Blogging with Jekyll Tutorial | Jekyll-Bootstrap](http://jekyllbootstrap.com/)
- [WordPressよりjekyllで本格的ブログを作りたくなる、かもしれないまとめ](http://tokkono.cute.coocan.jp/blog/slow/index.php/programming/making-blog-with-jekyll/)

---

[master](http://coderwall.com/crazymaster)
