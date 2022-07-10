# YOLOv5を用いたメダカ検出

## 概要
近頃、Youtuberがメダカの飼育方法を紹介するなど、メダカの人気が高まってきています。\
ヤフオクやその他ネット通販では、メダカの卵や成体が盛んに売買されており、有名なブリーダーが品種改良で作成したメダカは特に高額で取引されている。\
しかしメダカの飼育に関してはまだまだアナログな部分が多く、自動化が進んでいない。\
そのため、大量のメダカを大きな水槽で飼っている場合、生存数の調査は大変であることが予想される。\
これを解決するためには、メダカの検出を自動でできるようにすることが考えられる。\
メダカの検出を自動で行うことは、メダカの匹数算出の他、弱っているメダカの検出や、交配に必要な雌雄判定、品種判定などにも貢献できると予想される。\
これらの問題に取り組む一歩として、今回は物体検出アルゴリズムであるYOLO(You Only Look once)v5を使ってメダカの検出に取り組んだ。
## モデル作成について
YOLOv5の転移学習には自作のデータセットを構築した。\
データはGoogle上からスクレイピングすることで約200枚の画像を取得し、クレンジングを行って約170枚ほどになった。\
そのデータに対して、Microsoft社が無償提供している画像アノテーションソフトウェアVoTT(https://github.com/microsoft/VoTT)
を使用して、メダカに教師信号を付与した。\
今回ラベルはmedakaの１つだけを設定して、アノテーションを行った。\
その後、アノテーションデータをYOLOv5用の入力形式に変換するためにroboflow(https://roboflow.com/)
のサービスを利用してデータセットを構築した。
このデータセットを用いてYOLOv5を転移学習した。

## 利用方法
このリポジトリをコピーする。
モデルのパラメータ(https://github.com/tsutsui6Electronics/medaka-detection/releases/tag/YOLOv5_medaka-detection)
をダウンロードし、コピーした`medaka-detection/`に展開する。
その後jupyter notebook形式のプログラムを実行する。
前半は1枚の画像に対して、後半は動画に対してメダカの検出を行うプログラムになっています。

## 備考




