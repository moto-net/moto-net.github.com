---
layout: post
title: OpenGLを使ってゲームを作ろう
category: Programming
tags: [ OpenGL, oyas ]
tagline: 3Dゲームプログラミングに挑戦
---

<font color="red">2013/5/12 インストールの項目を修正。Windowsへのインストール方法を確認して載せました。</font>

こんにちは、oyasです。今回は、OpenGLを使ってのゲーム作りに挑戦します。
といっても、ほぼ参考サイトの紹介となります。

まあ、それだけでは記事にならないので、簡単なゲームを作りましたので、そのコードを追っかけながらやっていくといいでしょう。

本当は、去年の文化祭で作った[ゲーム](https://github.com/oyas/SKSunshine)の解説をやりたかったのですが、
量が多いのと、流れをつかむだけなら、簡単なゲームを作りながらやったほうがいいのではないかと思ったので、
今回はそうします。




もちろん、OpenGLのゲームの実装の方法はいろいろあるわけで、今回紹介する方法が一番いいというわけではありません。
ほんの一例と捉えてください。
どんなゲームを作るかによってだいぶかわったりもしますし。
ある程度分かってきたら自分で考えてみると楽しいと思いますよ。



この講座を読むにあたって、予備知識としては、C/C++の知識がいります。
しかし、ここではC++はクラスの機能くらいしか使わないので、C言語ができればほぼ問題ないです。
そもそも僕がこのゲーム作りに取りかかったときは、C言語の知識しか持っていませんでした。
C++とOpenGLは、作りながら習得していった感じで、あまり深いことはしてないので、C言語さえ完璧ならいけるとおもいます。
分からない場合は調べながら進めていくといいでしょう。


--------

参考サイトの紹介
------

[GLUTによる「手抜き」OpenGL入門](http://www.wakayama-u.ac.jp/~tokoi/opengl/libglut.html)  
OpenGLの入門サイトです。ここから読み始めるといいでしょう。
ここの内容をひと通り読み終えたら、下のゲームのコードを読むことができると思います。

[OpenGL入門](http://wisdom.sakura.ne.jp/system/opengl/index.html)  
詳しいです。僕はわかないことが出てきたらよくここで調べていました。

[OpenGL de プログラミング](http://wiki.livedoor.jp/mikk_ni3_92/)  
サンプルコードがたくさんあります。

[Project Asura](http://asura.iaigiri.com/program.html)  
いろいろなことをやっています。高度なエフェクトとかも。
Xファイル読み込みの実装の時にも参考にさせてもらいました。

[ゲームプログラマーを目指すひと](http://rudora7.blog81.fc2.com/blog-entry-310.html)  
Xファイル読み込みの実装の時に参考にさせてもらいました。

[OpenGLプログラミングメモ](http://www21.atwiki.jp/opengl/)  
現在も更新中。僕はほとんど見なかったのですが、だいぶ参考になると思います。

[ゲームつくろー！](http://marupeke296.com/GameMain.html)  
いろいろ詳しいです。衝突判定はここを参考にしました。

[OpenGLと行列について](http://www.slideshare.net/miyosuda/opengl)  
OpenGLをやってると目にする「行列」や、OpenGLの内部処理に興味を持ったら見てください。


------------

コンパイルできる環境の用意
------

OpenGLのゲームを作るために必要なものを揃えましょう。

必要なもの（下のサンプルゲームを動かすだけなら最初の２つだけでOK）

- g++	・・・　C++のコンパイラ。
- GLUT	・・・　ウィンドウの表示。OpenGLの補助機能。今回は互換性のあるfreeglutを使う。
- ALUT	・・・　サウンド再生。BGMの再生用。

###Ubuntuにインストール

端末を開いて、以下のコマンドを入力してください。

```bash
$ sudo apt-get install freeglut3 freeglut3-dev g++
```
	
これで下で紹介するサンプルゲームは動きますが、「SKSunshine」を動かしたい場合は、さらにOpenALのインストールが必要です。端末で続けて以下のコマンドを実行します。

```bash
$ sudo apt-get install libalut-dev
```
	


###Windowsにインストール


#### MinGWのインストール

WindowsではMinGWを使ってコンパイルしたいと思うので、まずそれをインストールしてください。
MinGWは、フリーのコンパイラであるGCCを、Windowsアプリケーションの開発のために利用できる。（Wikipedia）とあります。GCCはUbuntuに標準で含まれているコンパイラです。
要は、WindowsでもUbuntuと同じように開発できるようにしましょう、ということです。

参考サイト  
<http://yoshiiz.blog129.fc2.com/blog-entry-383.html>

インストール手順

1. MinGWのサイトでインストーラーを入手
	
	<http://sourceforge.net/projects/mingw/files/Installer/mingw-get-inst/>  
	中程にある「Looking for the latest version?」の横にあるリンクからダウンロードページへ行ってください。2013/05/12時点では「Download mingw-get-inst-20120426.exe(662.7kB)」というリンクになっています。

2. インストーラーを起動。
	
	ダウンロードした実行ファイルを起動するとこんな感じです。  
	![](http://dl.dropbox.com/s/x4ca64jk3bdfwvh/01.png)

3. NEXTを押しまくる
	
	Welcome to The MinGW-Get Setup Wizard

	↓ NEXT

	Administrator Install

	↓ NEXT

	Repository Catalogues  
	パッケージを最新版のにするか聞かれるが、最新のインストーラーなら必要ないのでそのままにしておく。
		
	↓ NEXT

	License Agreement  
	「I accept the agreement」を選択する。

	↓ NEXT
	
	Select Destination Location  
	MinGWのインストール先フォルダを聞かれる。初期設定でいいと思います。
	(1.9GB以上の空き領域が必要だそうです)
		
	↓ NEXT
	
	Select Start Menu Folder  
	スタートメニューに指定した名前のフォルダを作ります。
	そこへ「MinGW Shell」へのリンクが作られます。
	下のチェックボックスにチェックをいれると、フォルダを作りません。
		
	↓ NEXT
	
	Select Components  
	![](http://dl.dropbox.com/s/ljiwju6u4govhcj/02.png)  
	「C++ Compiler」「MSYS Basic System」「MinGW Developer ToolKit」の３つにチェックをいれます。
	ちなみにここで選択しなかったものも後でmingw-getコマンドで追加できます。
		
	↓ NEXT
	
	Ready to Install

	↓ NEXT
	
	黒い画面が出ますが、怖がらずに見守りましょう。  
	![](http://dl.dropbox.com/s/1k4ylg6o9fu7fij/03.png)
	
	↓ 
	
	Completing the MinGW-Get Setup Wizard
	
	↓ Finish
	
	終わり。最後のチェックをいれてると、黒い画面に表示されてた内容がテキストエディタで開かれます。


4. 環境変数の設定

	しなくても大丈夫ですが、設定すると、コマンドプロンプトからMSYSと同じコマンドが使えたり、DLLを実行ファイルと同じフォルダに入れておかなくても、C:\MinGW\bin等へ入れておけばいいようになります。

	システムのプロパティ→「詳細設定」タブ→「環境変数」ボタン から設定できます。環境変数「PATH」の最後に「;C:\MinGW\bin;C:\MinGW\msys\1.0\bin」を追加します。

5. 実行できるか確認

	スタートメニューの「MinGW」→ 「MinGW Shell」 でMSYSが起動すればOK。

	![](http://dl.dropbox.com/s/akub8n4szgkc6wp/05.png)


#### fleeglutのインストール

以下のページからバイナリファイルをダウンロードしてきましょう。

<http://www.transmissionzero.co.uk/software/freeglut-devel/>

「freeglut 2.8.1 MinGW Package」のとこの「Download freeglut 2.8.1-1 for MinGW」のリンクをクリックするとダウンロードできます。
バージョン番号は変わっているかもしれません。

展開したあと、中身の「bin」「lib」「include」をC:\MinGW\以下へコピーしてください。
このとき各フォルダの中の「x64」フォルダは、コピーしないでください。
(僕の環境は64bitでしたが、うまく動かなかったんで、今回はどの環境でも「x64」フォルダの中身は使わないことにしましょう。)

これでfreeglutのインストールは完了です。

ここまでで、下に載せたサンプルゲームは動きます。

SKSunshineを動かしたい場合は、つづけて「OpenAL」もインストールしましょう。





#### その他のインストール
<font color="red">近日訂正予定</font>

これで下で紹介するサンプルゲームは動きますが、「SKSunshine」を動かしたい場合は、さらにOpenALのインストールが必要です。

OpenALのインストールはここを参考に。

[mingwでALUTを用いたOpenALのコンパイル方法](http://island.geocities.jp/v_no11/programing/OpenAL.html)

おそらく  
「OpenAL SDK」　→　「oalinst」  
「freealut Binary Zip」　→　「ALUT/freealut-1.1.0-bin」  
と読みかえればいけると思います。

ちなみに、「alut.dll」「OpenAL32.dll」は、ゲームの実行ファイルと同じディレクトリに入れても動きます。



それと、GLEWも必要だった気がするので入れておきましょう。  
[MinGWでglewを入れる](http://d.hatena.ne.jp/Inuneco/20110716/p1)

----------

簡単なゲーム
------

ソースコードはここにおいておきます。  
[OpenGLGame](https://github.com/oyas/OpenGLGame)

詳しい解説はできませんが、根気よくやれば読めるはずです。

###とりあえず動かしてみよう

まずは、上に載せたリンク先で、ソースコードをダウンロードします。
「OpenGLをつかった簡単なゲーム」と書かれたとこの下の「ZIP」をクリックすればダウンロードできます。

#### Ubuntuで動かす

端末を開いて、先程ダウンロードしたZIPを展開したディレクトリに移り、以下のコマンドを実行します。

	$ make
	$ ./a.out

これでゲームが起動すれば成功です。

#### Windowsで動かす

展開したものを「C:\MinGW\msys\1.0\home\(ユーザー名)\」へ移します。
フォルダ名は「OpenGLGame」に改名してください。
MSYSを起動し、以下のコマンドを入力します。

	$ cd OpenGLGame
	$ make win
	$ a.exe
	
これでゲームが起動すれば成功です。  

![](http://dl.dropbox.com/s/p08vc7oy7t0xw2f/04.png)

ちなみに、操作方法は以下のとおりです。

	w : 前進
	s : 後退
	a : 左回転
	d : 右回転
	スペースキー : ジャンプ

時間内にどれだけ多くの赤い箱をとれるかというゲームです。

###ソースの読み進め方

####tagを使って追う

![](http://cloud.github.com/downloads/moto-net/moto-net.github.com/2012-11-12_02.png)

図の赤い四角で囲まれたとこを順にクリックしていきます。タグ一覧が表示されるので、読みたいタグをクリックしてください。すると、そのときのリポジトリに変わります。

![](http://cloud.github.com/downloads/moto-net/moto-net.github.com/2012-11-12_04.png)

特定のtagのときのソースをダウンロードできます。

####commitを追う

![](http://cloud.github.com/downloads/moto-net/moto-net.github.com/2012-11-12_01.png)

図の赤い四角で囲まれたとこをクリックします。

![](http://cloud.github.com/downloads/moto-net/moto-net.github.com/2012-11-12_03.png)

commit一覧が表示されます。今黄色くなっているコミットでいうと、「Makefile追記」または「fid48685f9」をクリックすると、前回のコミットとの差分が表示できます。
赤い四角で囲まれたとこをクリックすると、そのときのソース全体が表示できます。

----------------------

OpenGLは、機能としてはほぼ「ポリゴンを表示する」しかないので、モデルファイルを読み込むことや、物理運動をさせることなどは、すべて自分で実装しなければなりません。そこが大変で楽しいところです。
ぜひ、いい3Dゲームを完成させてください。

[oyas](http://coderwall.com/oyas)

