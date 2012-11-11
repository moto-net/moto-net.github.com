---
layout: post
title: OpenGLを使ってゲームを作ろう
category: Programing
tags: [ OpenGL ]
tagline: 3Dゲームプログラミングに挑戦
---


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
- glpng	・・・　png画像の読み込み。

###Ubuntuにインストール

端末を開いて、以下のコマンドを入力してください。
	
	$ sudo apt-get install freeglut3 freeglut3-dev g++
	
これで下で紹介するサンプルゲームは動きますが、「SKSunshine」を動かしたい場合は、さらにOpenALとglpngのインストールが必要です。端末で続けて以下のコマンドを実行します。(glpngのパッケージはないみたいなので手動インストールとなります)

	$ sudo apt-get install libalut-dev
	$ mkdir /tmp/glpng
	$ cd /tmp/glpng
	$ wget ftp://ftp.usa.openbsd.org/pub/OpenBSD/distfiles/glpng-1.45/glpng.zip
	$ unzip glpng.zip
	$ cd src/
	$ make -f Makefile.LINUX
	$ cd ../
	$ sudo cp lib/libglpng.a /usr/lib/
	$ sudo cp include/GL/glpng.h /usr/include/GL/


###Windowsにインストール

Windowsにインストールしたのはだいぶ前で、どういれたのか忘れてしまいました。
そして今はWindowsが使えない状態なので、確認ができません。
ネットでそれらしい情報はさがしたのですが、うまくいくかは未確認です。すみません。

#### MinGWのインストール

WindowsではMinGWを使ってコンパイルしたいと思うので、まずそれをインストールしてください。
MinGWは、フリーのコンパイラであるGCCを、Windowsアプリケーションの開発のために利用できる。（Wikipedia）とあります。GCCはUbuntuに標準で含まれているコンパイラです。
要は、WindowsでもUbuntuと同じように開発できるようにしましょう、ということです。
インストールは以下のページを参考にしてください。

[Windows 7にMinGWをインストールする(mingw-get-inst使用)](http://symfoware.blog68.fc2.com/blog-entry-797.html)

[ODE講座２：インストール（フリーのWindows開発環境：MinGW)](http://demura.net/9ode/326.html)  
ODEのインストールは必要ないです。

[MinGWとGLUTとGLUIでOpenGL始めよう！](http://oni-zine.net/?p=745)

[Windows で MinGW バージョン 20110530 のインストールとテスト実行](http://www.kkaneko.com/rinkou/cygwin/mingw.html)

リンク切れしてたり、内容が変わってたりするのもありますね。。

MinGWのダウンロードページは、わかりにくいかもしれませんが、おそらく、  
<http://sourceforge.net/projects/mingw/files/Installer/mingw-get-inst/>  
の中の最新版の.exeファイルがインストーラーだと思うのでそれをダウンロードしてください。

ちなみに、「MinGW base tools」 「g++ compiler」 「MinGW Make」は必須ですので、
MinGWのインストール中にチェックをいれるのを忘れないようにしてください。

MSYSは、MinGWのインストーラーからインストールできるみたい（？）です。

MSYSはいらないのかな。かもしれないです。インストール方法がわからなかったらとばしましょう。


#### fleeglutのインストール

[MinGWでOpenGLやGLUTを使ってみる](http://d.hatena.ne.jp/tana-laevatein/20091227/1261942906)

バージョンが2.8.0に上がっているみたいですね。

最後、freeglut.dllをどこかパスが通っているフォルダに入れるのですが、どこかわからなかったら、
ゲームの実行ファイルと同じディレクトリでもいいです。


#### その他のインストール

これで下で紹介するサンプルゲームは動きますが、「SKSunshine」を動かしたい場合は、さらにOpenALとglpngのインストールが必要です。

OpenALのインストールはここを参考に。

[mingwでALUTを用いたOpenALのコンパイル方法](http://island.geocities.jp/v_no11/programing/OpenAL.html)

おそらく  
「OpenAL SDK」　→　「oalinst」  
「freealut Binary Zip」　→　「ALUT/freealut-1.1.0-bin」  
と読みかえればいけると思います。

ちなみに、「alut.dll」「OpenAL32.dll」は、ゲームの実行ファイルと同じディレクトリに入れても動きます。

glpngのインストールはおそらく先程とほぼ同じ方法でいけます。コマンドプロンプトから、

	$ mkdir tmp
	$ cd tmp
	$ wget ftp://ftp.usa.openbsd.org/pub/OpenBSD/distfiles/glpng-1.45/glpng.zip
	$ unzip glpng.zip
	$ cd src/
	$ make -f Makefile.LINUX
	$ cd ../
	$ sudo cp lib/libglpng.a C:/MinGW/lib/
	$ sudo cp include/GL/glpng.h C:/MinGW/include/GL/
	$ cd ../
	$ rm -rf tmp/

wgetが使えない場合は手動でダウンロード、unzipが使えない場合は手動で解凍してください。

それと、GLEWも必要だった気がするので入れておきましょう。  
[MinGWでglewを入れる](http://d.hatena.ne.jp/Inuneco/20110716/p1)

----------

簡単なゲーム
------

ソースコードはここにおいてあります。  
[OpenGLGame](https://github.com/oyas/OpenGLGame)

詳しい解説はできませんが、根気よくやれば読めるはずです。

###読み進め方

####tagを使って追う

![](http://cloud.github.com/downloads/moto-net/moto-net.github.com/2012-11-12_02.png)

図の赤い四角で囲まれたとこを順にクリックしていきます。タグ一覧が表示されるので、読みたいタグをクリックしてください。すると、そのときのレポジトリに変わります。

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

oyas

