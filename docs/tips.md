# 豆知識

## n小節目のBPM/BEATが知りたい

sus-analyzerで取得したBPM/BEATを一度配列にし、その配列から該当する小節を取り出します。
結果があればそのBPM/BEATを、結果が空なら小節数を1引いてもう一度取得。を繰り返すと取得できます。

## susの解析/走査について

本家の解析方法が文書化されていない為明確な差は分かりませんが、sus-analyzerの解析について書いておきます。参考になる事があれば幸いです。

### メタデータ
ファイルの上から順に1行づつ解析します。   
同じ項目が複数現れた場合、後者で上書きされます。

### ショートノーツ
ファイルの上から順に1行づつ解析します。   
ただただそれだけです。

### ロングノーツ
ノーツをtick毎に分け、ループを回します。

該当1tick辺り3回処理をします。
1. そのノーツが終了点である（最優先・controlをまとめてロングノーツを返す）
2. そのノーツが中継点である（controlに入れてcontinue）
3. そのノーツが開始点である（idを紐づけて配列に）

