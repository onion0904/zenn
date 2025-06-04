---
title: "並行処理を使って画像処理[golang]"
emoji: "🏎️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["go","image","concurrency"]
published: true
---

# まず
こちらの記事は私が足りていないと思う所を重点的に勉強する。
onion7日間チャレンジのDay2になります。
詳しくは[ここ](https://zenn.dev/onion0904/articles/ff700890522030)の冒頭で書いてあるので気になる人は見てみてください。
Day1↓
@[card](https://zenn.dev/onion0904/articles/ff700890522030)


# 作ったもの
Day2ではGoでは必須な並行処理の知識が足りていないと感じていたので、
ディレクトリの画像のサイズを変更するCLIツールを作成しました。
名前はresizon(resize+onion)ということにしました。
@[card](https://github.com/onion0904/day-two-concurrency)

## 作ったものの概要 
resizon(標準入力から操作)
jpegとpngに対応しています。
resizonは一つ一つの画像を並行処理しているため、高速に画像のサイズを変更することができます。


## 実際にやってみる
![](https://storage.googleapis.com/zenn-user-upload/cae8ff1310c9-20250605.jpg =400x)
*元画像*

実行する
```
go run main.go
input create of image directory: ./output //出力先のファイルパス
input path of image directory: ./images //元画像のディレクトリのパス
input size: 600 600//変更するサイズ
```

![](https://storage.googleapis.com/zenn-user-upload/86921fb1274c-20250605.jpg =400x)
*サイズが変更された画像*


## サイズについて
### サイズが一つの場合

アスペクト比を維持したまま出力します。
```
input size: 100
```
この時は元画像の短い辺を100pxにして、長い辺を元の画像の比に合わせるように変更します。

### サイズが二つの場合
横、縦の順で入力されます。
```
input size: 100 200
```
横100px,縦200px


# 学んだこと
画像処理と並行処理のやり方を深くではないが、知ることができた。
並行処理に関しては、以下にまとめた
@[card](https://github.com/onion0904/day-two-concurrency/tree/main/docs)


## 参考資料
[Goの並行処理入門](https://tech.yappli.io/entry/goroutine-base)

[画像処理](https://blanktar.jp/blog/2024/01/golang-resize-image)