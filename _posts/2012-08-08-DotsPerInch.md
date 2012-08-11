---
layout: post
title: 画像の解像度のハナシ
category: Graphics
tags: [ コンピュータグラフィックス, 初心者向け, ensosarashi ]
tagline: 覚えておきたいデジ絵の知識
---

![](http://cloud.github.com/downloads/ensosarashi/Icon/mado_n.png)「保健係の仕事でポスターを作ることになったよ！」

![](http://cloud.github.com/downloads/ensosarashi/Icon/homu_n.png)「まどか、ポスターの絵はパソコンで描くつもりかしら？」

![](http://cloud.github.com/downloads/ensosarashi/Icon/mado_n.png)「うん、今回はパソコンでポスター作りに挑戦しようと思うんだ」

![](http://cloud.github.com/downloads/ensosarashi/Icon/homu_n.png)「それなら。今回はデジタル画像の解像度について説明しましょう」

![](http://cloud.github.com/downloads/ensosarashi/Icon/mado_n.png)「わーい！」

##**目次**

>1. 解像度とは
>2. 主に利用される解像度の数値
>3. 実践編
>4. まとめ

　

##**1.解像度とは**

----------

![](http://cloud.github.com/downloads/ensosarashi/Icon/homu_n.png)「まずは、解像度とは何かを説明するわ」

解像度とは、ビットマップ画像におけるピクセルの密度を表す言葉です。

私たちが住む世界では、大きさ、形状、色など、全ての情報が連続した物理量に対応付けられて表現されています。この概念をアナログといいます。しかし、コンピュータ上で扱うデータは、情報が量子化、離散化されて段階的に表現されています。この概念をデジタルといいます。

解像度は、デジタルの段階的なデータ表現が、どれだけ細かい部分まで表現されているかの指標となる数値です。１インチ当たりのピクセル数で表現され、単位はdpi（ドット・パー・インチ）です。

解像度は、画像ファイルの縦と横の大きさと対応する部分もあるので、混同されてしまいがちですが、先の説明のとおり、異なる概念ですので気をつけてください。

![](http://cloud.github.com/downloads/ensosarashi/Icon/mado_n.png)「ほむらちゃん、説明が難しくてよく分からないよ」

解像度をアバウトに説明すると、画像の綺麗さを表す度合で、解像度が高ければ高いほど画像が綺麗になります。下の図は、異なる解像度の写真を、画面上で同じサイズで表示したものです。解像度が高い方が画像が鮮明なのがよく分かると思います。

![](http://cloud.github.com/downloads/moto-net/moto-net.github.com/comparison.jpg)

　

##**2.主に利用される解像度の数値**

----------

![](http://cloud.github.com/downloads/ensosarashi/Icon/homu_n.png)「主に利用される解像度の数値を教えておくわ」

- 72dpi

	かつてのディスプレイの標準的な解像度。デジタル上でしか扱わない画像データはこれで十分。

- 300dpi

	アメリカの印刷業界で主流な解像度。日本の出版社もこの数値を採用している場合がある。

- 350dpi

	日本の印刷業界で主流な解像度。画像データの出力を想定する場合、この数値に設定しておくのがベスト。

- 600dpi

	比較的高めの解像度。それなりのデータ量になる。繊細なモノクロ原稿の出力や、高品質で印刷したい場合はこちら。

![](http://cloud.github.com/downloads/ensosarashi/Icon/mado_n.png)「おもいっきり高解像度に設定するのはダメかな？」

1000dpiなどの高い解像度になると、必然的にコンピュータ上で扱うデータの量も大きくなります。それに加え、出力の際に、高解像度に対応したプリンターでなければ、せっかくの高解像度も再現されません。さらには、ヒトの目で視認できないレベルの解像度で再現されても意味がありません。大は小を兼ねると言いますが、適切な数値に設定するのがベストです。

　

##**3.実践編**

----------

![](http://cloud.github.com/downloads/ensosarashi/Icon/homu_n.png)「まずは最終的に出力する方法を確認しましょう」

現在、出版社や印刷業社に、画像のデータをデジタル入稿するという形式が増えてきました。これらの場合、出版社や印刷業社側から、入稿する画像データの解像度を指定される場合があります。解像度を間違えると後が面倒なことになりかねないので、デジタル入稿する場合は、先にそれらの情報をよく確認しておきましょう。

一般の人が家庭や学校のプリンターで印刷する場合は、解像度は300dpiか350dpiに設定しておけば大丈夫でしょう。

![](http://cloud.github.com/downloads/ensosarashi/Icon/mado_n.png)「まずは線画をスキャンしたいな」

スキャナで線画を取り込む際に解像度の設定は重要になります。線画を綺麗に取り込むには、最終的に出力する画像のサイズに対応した解像度に設定しなければなりません。

取り込む線画の紙のサイズが、最終的に出力する紙のサイズと同じであれば、取り込みの際の解像度も同じで問題ありません。しかし、最終的に出力する紙のサイズが、取り込む線画の紙のサイズより大きい場合、サイズの比率に合わせて解像度を大きくしてやる必要があります。

ただし、スキャナで線画を取り込む際、解像度が高めに設定されているとスキャンに時間がかかります。線画がラフなもので、清書をコンピュータ上で行うなら、解像度を下げて取り込んだ方が時間もかかりませんし、データの容量も小さくて済みます。

![](http://cloud.github.com/downloads/ensosarashi/Icon/homu_n.png)「お絵かきソフトの解像度の設定も忘れないで」

お絵かきソフトで新規ファイルを作成する際、カンバスサイズと一緒に解像度を設定する項目があるはずです。解像度は後からでもいじれますが、低解像度から高解像度に変換するのはよろしくありません。最初に目的の解像度に設定しておくのがベストです。なお、Windouw標準のMSペイントの解像度は96dpiで、変更はできないみたいです。

![](http://cloud.github.com/downloads/ensosarashi/Icon/mado_n.png)「作品ができたら、いよいよ出力だね」

出力する紙のサイズを想定し、最初に設定をちゃんとしておけば、出力の際に困ることはほとんどないでしょう。

ただし、印刷の際には紙に余白ができます。もし、A4ぴったりのサイズを出力したいときには、一回り大きなB4の紙に印刷して裁ち落す必要があります。しかし、家庭用のプリンタだと出力サイズがA4までのプリンタも多いので、その場合は印刷設定で四辺フチなしを選択すれば、少しはみだす代わりに紙の余白をなくすことができます。

　

##**4.まとめ**

----------

![](http://cloud.github.com/downloads/ensosarashi/Icon/homu_n.png)「どう？少し難しかったけど解像度について理解できたかしら？」

![](http://cloud.github.com/downloads/ensosarashi/Icon/mado_n.png)「とりあえず、350dpiに設定しておけばいいことはわかったよ」

![](http://cloud.github.com/downloads/ensosarashi/Icon/homu_n.png)「そう。そこを覚えてもらえただけでも、話したかいがあったわ」

![](http://cloud.github.com/downloads/ensosarashi/Icon/mado_n.png)「アナログとデジタルのやり取りってなんだか難しいね。」

![](http://cloud.github.com/downloads/ensosarashi/Icon/homu_n.png)「難しいからこそ、知っておけば他の人と差をつけられるわ」

![](http://cloud.github.com/downloads/ensosarashi/Icon/mado_n.png)「なら、今回の講座で私も一歩リードだね！ｳｪﾋﾋw」

![](http://cloud.github.com/downloads/ensosarashi/Icon/homu_n.png)「今回の講座で分かりにくい所があれば、コメントしてくれれば可能な限りで答えるわ」

![](http://cloud.github.com/downloads/ensosarashi/Icon/mado_n.png)「ありがとう、ほむらちゃん！」

　

----------

記事作成：ensosarashi