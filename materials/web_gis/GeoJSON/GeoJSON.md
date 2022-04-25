# GeoJSON
　本教材は、WEBマップで利用する代表的なデータであるGeoJSONについて、入門者向けに解説したものです。以下では、テキストエディタを用いて、点、線、面のようなジオメトリやデータの属性情報の記述手法について解説しています。この教材は、北崎 茂 氏が日本語訳し`GeoJSON フォーマット仕様(http://s.kitazaki.name/docs/geojson-spec-ja.html#id4)`( geojson-spec.html © 2008 by Howard Butler (Hobu Inc.) , Martin Daly (Cadcorp) , Allan Doyle (MIT),
Sean Gillies (UNC-Chapel Hill) , Tim Schaub (OpenGeo), Christopher Schmidt (MetaCarta) CC-BY 3.0 US.)を参考に作成したもです。本教材は、入門者向けのものであるため、細かい説明を省略した個所があります。各項目の詳細については、上記のリンク先を参照ください。

本教材を使用する際は、[利用規約]をご確認いただき、これらの条件に同意された場合にのみご利用下さい。

**Menu**
--------
- [GeoJSONとは](#geojosnとは)
- [GeoJSONオブジェクト](#geojsonオブジェクト)
- [点データの作成](#点データの作成)
- [線データの作成](#線データの作成)
- [面データの作成](#面データの作成)
- [スタイリング](#スタイリング)


## GeoJSONとは
　GeoJSONは、JavaScript Object Notation (JSON) を基とした、GISデータを記述するためのフォーマットです（地理空間データ交換フォーマット）。この形式では、`Point, LineString, Polygon, MultiPoint, MultiLineString,MultiPolygon,GeometryCollection`をサポートしています。軽量言語であり、Web GISでの利用例が多く見られます。GitHubには、GeoJSONの地図表示機能があり、リポジトリにデータを配置するだけで可視化が可能です。以下では、GeoJSONで点、線、面を記述する手法について解説します。

　なおGeoJSONの標準的な仕様は、[RFC7946](https://datatracker.ietf.org/doc/html/rfc7946)に詳しく記述されています。

## GeoJSONオブジェクト
　GeoJSONのデータは、メンバー（名前と値）の集合体であるオブジェクトとして構成される。オブジェクトには、ジオメトリオブジェクト（coordinatesが必要）、フィーチャーオブジェクト（geometry, propertiesが必要）、フィーチャーコレクションオブジェクト(featuresが必要)などがある。以下では、ジオメトリオブジェクトを中心に解説する。ジオメトリオブジェクトには、typeがPoint, LineString, Polygon, MultiPoint, MultiLineString,MultiPolygon,GeometryCollectionが選択でき、GeometryCollection以外は、測地座標系を示すcoordinatesをもつ。

## 点データの作成
　以下では、点の記述手法について解説します。任意のテキストエディタを開き、新規ファイルを作成後、`.geojson`の拡張子で保存してください。

### 1地点の場合（富士山の山頂周辺を表示）
GeoJSONで1地点のポイントレイヤを作成する際は、以下のように記述する。

```JSON
{ "type": "Point",
  "crs": { "type": "name",
    "properties": {
      "name": "urn:ogc:def:crs:OGC:1.3:CRS84"
       }
      },
  "coordinates": [138.7309, 35.3628]
 }

```

* 最初のtypeは、"Point", "MultiPoint", "LineString", "MultiLineString", "Polygon", "MultiPolygon", "GeometryCollection", "Feature", および "FeatureCollection"のいずれかになる
* 上記の"crs"は、Named CRSとし、"properties"からWGS84を指定した
* "coordinates"は、経度、緯度、（高度）の順で並べる

作成したファイルをGitHubなどのビューワーで表示すると[完成例1]のようになる。

※ GeoJSONは、QGIS等でもインポートできるため、実習環境に合わせて適切なものを使用すると良い。


### 2地点の場合（富士山と愛鷹山の山頂周辺を表示）

```JSON
{ "type": "MultiPoint",
  "crs": { "type": "name",
    "properties": {
      "name": "urn:ogc:def:crs:OGC:1.3:CRS84"
       }
      },
  "coordinates": [[138.7309, 35.3628],[138.8079, 35.1983]]
 }

```

* 最初の"type"を"MultiPoint"にする
* "coordinates"に、愛鷹山の位置情報を追加

作成したファイルをGitHubなどのビューワーで表示すると[完成例2]のようになる。


### 2地点の場合：FeatureCollectionで表示
複数のフィーチャーを同ファイル内に記述する場合、以下のように"FeatureCollection"を使用する。

```JSON
{ "type": "FeatureCollection",
  "crs": { "type": "name",
    "properties": {
      "name": "urn:ogc:def:crs:OGC:1.3:CRS84"
       }
      },
  "features": [
    { "type": "Feature",
      "properties": { },
      "geometry": {
         "type": "Point",
         "coordinates": [138.7309, 35.3628]
 }},
    { "type": "Feature",
       "properties": { },
       "geometry": {
          "type": "Point",
          "coordinates": [138.8079, 35.1983]
  }}
  ]
}

```


### 属性情報の記述
属性情報は、以下のように"features"の下層の"properties"に記述する。

```JSON
{ "type": "FeatureCollection",
  "crs": { "type": "name",
    "properties": {
      "name": "urn:ogc:def:crs:OGC:1.3:CRS84"
       }
      },
  "features": [
    { "type": "Feature",
      "properties": { "id": 1, "name": "fujisan" },
      "geometry": {
         "type": "Point",
         "coordinates": [138.7309, 35.3628]
 }},
    { "type": "Feature",
       "properties": { "id": 2, "name": "ashitakayama" },
       "geometry": {
          "type": "Point",
          "coordinates": [138.8079, 35.1983]
  }}
  ]
}
```

作成したファイルをGitHubなどのビューワーで表示すると[完成例3]のようになる。


## 線データの作成
線は、"type"に"LineString"を選択し、以下のように記述する。

```JSON
{ "type": "LineString",
  "crs": { "type": "name",
    "properties": {
      "name": "urn:ogc:def:crs:OGC:1.3:CRS84"
       }
      },
  "coordinates": [[138.7309, 35.3628],[138.8079, 35.1983]]
 }
```

作成したファイルをGitHubなどのビューワーで表示すると[完成例4]のようになる。

## 面データの作成
面は、"type"に "Polygon"を選択し、以下のように記述する。このとき、"coordinates"の「始点と終点の座標を同じにすること」と「[]の数」に注意する。

```JSON
{ "type": "Polygon",
  "crs": { "type": "name",
    "properties": {
      "name": "urn:ogc:def:crs:OGC:1.3:CRS84"
       }
      },
  "coordinates": [[[138.7309, 35.3628],[138.8079, 35.1983],[139.0248, 35.2248],[138.7309, 35.3628]]]
 }
```


作成したファイルをGitHubなどのビューワーで表示すると[完成例5]のようになる。


### 点、線、面を一つのGeoJSONで表示：FeatureCollectionで表示
以下のようにすると、一つのGeoJSONファイル内に、異なる形状のフィーチャーをまとめて記述することができる。

```JSON
{ "type": "FeatureCollection",
  "crs": { "type": "name",
    "properties": {
      "name": "urn:ogc:def:crs:OGC:1.3:CRS84"
       }
      },
  "features": [
    { "type": "Feature",
      "properties": { },
      "geometry": {
         "type": "MultiPoint",
         "coordinates": [[138.7309, 35.3628], [138.8079, 35.1983],[139.0248, 35.2248]]
 }
},
    { "type": "Feature",
       "properties": { },
       "geometry": {
          "type": "LineString",
          "coordinates": [[138.7309, 35.3628], [138.8079, 35.1983],[139.0248, 35.2248]]
  }},
     { "type": "Feature",
        "properties": { },
        "geometry": {
           "type": "Polygon",
           "coordinates": [[[138.7309, 35.3628],[138.8079, 35.1983],[139.0248, 35.2248],[138.7309, 35.3628]]]
   }}
  ]
}

```

作成したファイルをGitHubなどのビューワーで表示すると[完成例6]のようになる。

## スタイリング
以下では、GitHubを用いてGeoJSONをスタイリングする手法について解説します。GitHubでは、リポジトリに配置したGeoJSONを地図表示する機能が搭載されています。レイヤは、[mapbox/simplestyle-spec](https://github.com/mapbox/simplestyle-spec/tree/master/1.1.0)の条件でスタイリングすることができます。以下では、このリンクを参考にGeoJSONにスタイルを書き加え、GitHubで表示しています（"features"の下層に、"properties"を追加してスタイリングしている）。

> 詳しくは、https://help.github.com/articles/mapping-geojson-files-on-github を参照してください。

```JSON
{ "type": "FeatureCollection",
  "crs": { "type": "name",
    "properties": {
      "name": "urn:ogc:def:crs:OGC:1.3:CRS84"
       }
      },
  "features": [
    { "type": "Feature",
      "properties": { "id": 1, "name": "fujisan" },
      "geometry": {
         "type": "Point",
         "coordinates": [138.7309, 35.3628]
 },
 "properties": {
    "marker-color": "#363",
    "marker-size": "large",
    "title": "富士山",
    "description":"日本一高い山"
}},
    { "type": "Feature",
       "properties": { "id": 2, "name": "ashitakayama" },
       "geometry": {
          "type": "Point",
          "coordinates": [138.8079, 35.1983]
  }},
     { "type": "Feature",
        "properties": { "id": 3, "name": "komagatake" },
        "geometry": {
           "type": "Point",
           "coordinates": [139.0248, 35.2248]
   }}
  ]
}

```

作成したファイルをGitHubなどのビューワーで表示すると[完成例7]のようになる。

[▲メニューへもどる]

#### ライセンスに関する注意事項
本教材で利用しているキャプチャ画像の出典やクレジットについては、[その他のライセンスについて]よりご確認ください。

[その他のライセンスについて]:../../license.md
[▲メニューへもどる]:./GeoJSON.md#Menu
[完成例1]:https://github.com/gis-oer/datasets/blob/master/vector/geojson/sample1.geojson
[完成例2]:https://github.com/gis-oer/datasets/blob/master/vector/geojson/sample2.geojson
[完成例3]:https://github.com/gis-oer/datasets/blob/master/vector/geojson/sample3.geojson
[完成例4]:https://github.com/gis-oer/datasets/blob/master/vector/geojson/sample4.geojson
[完成例5]:https://github.com/gis-oer/datasets/blob/master/vector/geojson/sample5.geojson
[完成例6]:https://github.com/gis-oer/datasets/blob/master/vector/geojson/sample6.geojson
[完成例7]:https://github.com/gis-oer/datasets/blob/master/vector/geojson/sample7.geojson
[利用規約]:../../../policy.md
[利用規約]:../../../policy.md
[その他のライセンスについて]:../../license.md
[よくある質問とエラー]:../../questions/questions.md

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
