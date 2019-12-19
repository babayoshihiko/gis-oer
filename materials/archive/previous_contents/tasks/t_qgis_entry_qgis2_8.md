# 課題：GIS入門
　GISでは、地理空間情報の可視化、編集、分析などができます。この実習はGIS入門として、QGISを用いて地図の作成を行うものです。この教材は、GIS初学者およびQGISの初心者向けです。各課題の手順とGISオープン教材の[QGISビギナーズマニュアル]を参考に、完成例のような地図が作成できれば、完了となります。GIS初学者は、本教材を進める前に[GISの基本概念]教材を確認しておいてください。

### 課題用データ
課題用データ[fkuchiyama_sample.zip]をダウンロードしてください。

## QGIS入門
　この実習は、QGISとサンプルデータを用いたデータの可視化や地図のレイアウトに関するものです。QGISは、無償で利用できるオープンソースのGISです。[QGISビギナーズマニュアル]を参考にインストールした後、実習を進めてください。本課題と対応する教材は、[QGISビギナーズマニュアル]です。

### 課題
　平成26年8月豪雨後に実施した京都府福知山市でのフィールド調査（インタビュー）データを用いて、完成例のような地図を作成してください。また、作成する地図は、調査地点、凡例、方位、縮尺バー、タイトル等をレイアウトしたものとします。

### 完成例
![完成例](pic/tQ1.png)

### 手順

1. QGISに実習用データをを読み込む
2. タイルレイヤープラグインで地理院タイルを読み込む
3. 属性情報の確認をする　※属性テーブルや、選択ツールなどを用いて各地点ごとの水害の被害状況を確認する。
4. ポイントのスタイルを調整する
5. 地図をレイアウトする

※地図にタイトルを記載する方法：プリントコンポーザーから、新規ラベルの追加 > アイテムプロパティ > メインプロパティ（タイトル等の入力） > 外観,フォント（文字のサイズ調整)

### この課題を動画で学ぶ
　上記の手順を動画にまとめています。GISの操作に自信がない方におすすめの学習法です。動画はYoutubeで公開しているため、画面の大きさや再生速度等を調節して、ご利用ください（動画はQGIS2.8）。
<div style = "text-align: center;">
<iframe width="560" height="315" src="https://www.youtube.com/embed/xWmSe04Ubl4" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe></div>

[動画が再生されない場合はこちら](https://www.youtube.com/watch?v=xWmSe04Ubl4)

> この動画は、GIS実習オープン教材の内容を援用して作成したものです。教材の更新が動画内容の更新よりも優先されるため、紹介するサイトのレイアウト等が異なる箇所は、適宜GIS実習オープン教材を参照してください。動画内では第3者の著作物を引用という形で使用しています。著作者からの異議申し立てがあった場合は、速やかに当該部分を削除します。

#### 完成例で使用したデータ
本ページで使用しているデータの出典については、該当する教材よりご確認ください。

[利用規約]:../../../policy.md
[その他のライセンスについて]:../../license.md
[よくある質問とエラー]:../../questions/questions.md
[fkuchiyama_sample.zip]:https://raw.githubusercontent.com/gis-oer/datasets/master/vector/fkuchiyama_sample.zip

[GISの基本概念]:../../00/00.md
[QGISビギナーズマニュアル]:../../QGIS/QGIS.md
[GRASSビギナーズマニュアル]:../../GRASS/GRASS.md
[リモートセンシングとその解析]:../../06/06.md
[既存データの地図データと属性データ]:../../07/07.md
[空間データ]:../../08/08.md
[空間データベース]:../../09/09.md
[空間データの統合・修正]:../../10/10.md
[基本的な空間解析]:../../11/11.md
[ネットワーク分析]:../../12/12.md
[領域分析]:../../13/13.md
[点データの分析]:../../14/14.md
[ラスタデータの分析]:../../15/15.md
[傾向面分析]:../../16/16.md
[空間的自己相関]:../../17/17.md
[空間補間]:../../18/18.md
[空間相関分析]:../../19/19.md
[空間分析におけるスケール]:../../20/20.md
[視覚的伝達]:../../21/21.md
[参加型GISと社会貢献]:../../26/26.md

[地理院地図]:https://maps.gsi.go.jp
[e-Stat]:https://www.e-stat.go.jp/
[国土数値情報]:http://nlftp.mlit.go.jp/ksj/
[基盤地図情報]:http://www.gsi.go.jp/kiban/
[地理院タイル]:http://maps.gsi.go.jp/development/ichiran.html

[課題ページ_QGISビギナーズマニュアル]:../../tasks/t_qgis_entry.md
[課題ページ_GRASSビギナーズマニュアル]:../../tasks/t_grass_entry.md
[課題ページ_リモートセンシングとその解析]:../../tasks/t_06.md
[課題ページ_既存データの地図データと属性データ]:../../tasks/t_07.md
[課題ページ_空間データ]:../../tasks/t_08.md
[課題ページ_空間データベース]:../../tasks/t_09.md
[課題ページ_空間データの統合・修正]:../../tasks/t_10.md
[課題ページ_基本的な空間解析]:../../tasks/t_11.md
[課題ページ_ネットワーク分析]:../../tasks/t_12.md
[課題ページ_基本的な空間解析]:../../tasks/t_13.md
[課題ページ_点データの分析]:../../tasks/t_14.md
[課題ページ_ラスタデータの分析]:../../tasks/t_15.md
[課題ページ_空間補間]:../../tasks/t_18.md
[課題ページ_視覚的伝達]:../../tasks/t_21.md
[課題ページ_参加型GISと社会貢献]:../../tasks/t_26.md