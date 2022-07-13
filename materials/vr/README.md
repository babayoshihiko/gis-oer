# 地理情報を用いたVRアプリ開発入門
本教材ではUnityを使って、バーチャルな仮想空間を散歩するVRアプリを構築する手法を解説します。Unityを用いることで難しいプログラミングの知識がなくても、バーチャルリアリティ（VR）のアプリを構築できます。本教材では、PCで動作するWebGLアプリと、`Facebook社のMeta Quest 2`で動作するVRアプリの開発手順を説明します。本教材は、WebGLやVRアプリ・コンテンツ開発体験のための入門教材ですので、Unityの簡単な入門ガイドとしてご利用いただくことも可能です。

※　本教材の整備にあたり、東京大学CSIS客員研究員/フリーランスエンジニアの鶴岡謙一氏の協力を得ました。

## 本教材で解説するアプリの概観
本教材では、3D空間を歩いて韮山反射炉を眺めるアプリを開発します。3Dモデルを表示し、3D空間を移動できるシンプルな機能を有します。本教材では、このアプリについて、入門としてウェブブラウザで動作するWebGL版、応用としてMeta Quest 2で動作するVR版の開発手法を解説します。
`韮山アプリの動作の様子（アプリ画面の動画キャプチャ）`

![demo](./img/vr_demo.gif)

> 実習用データは、[30-XXX01-01-00-01　©静岡県ＰＣＤＢ　CC-BY](https://pointcloud.pref.shizuoka.jp/lasmap/ankenmap?ankenno=30XXX01010001)を改変し、作成しています。

## 学習に必要な機材

- PC（Windows 10）:　3Dモデルを処理しグラフィックス表示させるため、それに適した性能のPCが必要になります（筆者は、(OS:Windows 10, CPU:Intel Core i9 9900K, メモリ:32GB, GPU: nVidia RTS2080Ti(11GB))を使用）。本教材の解説は、Windowsによるものを対象とします。Mac、Linuxなどの他の環境は、本教材の説明対象ではありません。Unityは、Mac版やLinux版のUnityもありますが、学習・開発を進める場合、ご自身で設定したり、操作方法が必要になること、必ずしも動作させることができない可能性があることにご留意下さい。
- Meta Quest 2:　VRで体験する場合は必要です。必須ではありません。Oculusには他の機種もありますが、Meta Quest 2のみの動作を解説の対象とします。

※　注意点： Unity, Oculus, Windows 10などは、アップデートや新機能の追加が頻繁に行われております。このため、これらの仕様の変更や互換等が理由で、本教材のアプリが、本教材の方法ではうまく動作しないことや、バージョンによる不具合などの問題が起きることがあります。必ずしも動作しない可能性があることにご留意をお願いします。

## Unityについて
本教材では、Unityという開発ソフトウェアを使って開発を進めます。Unityとは、[Unity Technologies社](https://unity.com/ja/)が公開しているゲーム・アプリ開発ソフトウェアです。2004年にデンマークで発祥し、現在はサンフランシスコにUnity Technologies社の本社があります(日本法人は「ユニティ・テクノロジーズ・ジャパン株式会社」)。Unityは、ゲーム、学習アプリ、建築モデルを表示するデモンストレーションなど、様々な分野で活用されています。

### VR開発でUnityが利用されている理由
本来３Dモデルを処理するようなプログラミングを行ってアプリやゲームとして完成させることは、技術的にハードルが高く、相応の開発技能を要します。また、一から全て自分だけで開発することは労力・時間などのコストが膨大になりがちです。そこで、Unityというオールインワンの開発環境を使うことで、開発作業を簡素化・効率化することができます。3D処理、プログラミング、アプリとしてのビルド（出力）まで、基本的にUnityを使うだけで行うことも可能です（Unityだけでは難しいことは、Visual Studioなども利用します（後述））。

### Unityライセンスの注意
Unityは、商用の開発ソフトウェアのため、利用形態によっては利用料金が発生します。大学生が自身の学習・研究用に利用する用途での「Unity Free」（無料プラン）の利用を想定しています。自身の利用用途・所属などと、ライセンス規約をよく確認し、同意できる場合、Unityが使用できます。ライセンスは遵守して、自己責任で利用して下さい。

### 他の開発ソフトウェア
Unityの以外にも、アプリ・ゲームなどの開発ソフトウェアはいくつもあります。例えば、Epic社のUnreal Engineという開発ソフトウェアが有名です。Unreal Engineも世界中のゲームなどの開発で利用されています。Sony Interactive Entertainment社のPlayStation 5の初回発表会で、Unreal Engineで開発されたコンテンツのデモンストレーションが披露されました。Unreal Engineは、写実的な表現が高く、上手に実装すれば、まるで実写のような表現も可能です。ブループリントというダイアグラムを組み合わせて簡便にアプリを実装できる標準機能があることも特徴の一つです。UnityではC#言語を使ってプログラミングを行いますが、Unreal EngineではC++言語を使ってプログラミングを行います。一般的に、C++言語のほうが習得や利用により高度な知識が必要になるといわれています。他の開発ソフトウェアとして、Amazon lumberyard、CryEngineなどがあります。

## 学習項目と順序
本教材の解説は、以下のように分かれています。1から順に学習をはじめてください。

|学習順|項目|
|---|---|
|1| [Unityのインストールと初期設定](./vr1.md)|
|2| [Unityの基本画面と操作方法](./vr2.md)|
|3| [地理情報の取り込みと表示設定](./vr3.md)|
|4| [アセットの利用とアプリの調整](./vr4.md)|
|5| [テストとビルド](./vr5.md)|
|6| [VR開発の概要とMeta Quest 2の設定](./vr6.md)|
|7| [Meta Quest 2向けのUnityの初期設定](./vr7.md)|
|8| [歩行機能のプログラミング](./vr8.md)|
|9| [Meta Quest 2への転送と動作確認](./vr9.md)|