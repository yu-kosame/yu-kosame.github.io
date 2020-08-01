+++
date = "2019-04-07"
draft = false
title = "pix2pix による土地被覆分類 試行記録"
slug = ""
categories = ["study"]
tags = ["linux"]
+++

（編集中）

## GPU 搭載マシンを購入

NVIDIA の GPU（グラフィックボード）搭載のものを選びます。  
汎用のものより，ゲーミングマシンの用の GPU のほうがお手頃でした（Geforce など）。  
部屋のスペースを考えて，コンパクトな Dospara の [GALLERIA SZ](https://www.dospara.co.jp/5shopping/detail_prime.php?tg=13&tc=665&mc=8534&sn=0&tb=2) にして，GPU は GeForce GTX1080Ti のものにしました（今はもっとハイスペックのものがあるかも）。

## OS 別の環境構築：Windows

こちらの記事を参考にしました。  
[pix2pix を動かしてみる](https://www.kunihikokaneko.com/dblab/tensorflow/pix2pix.html)

## OS 別の環境構築：Ubuntu

デュアルブートにします。  
Windows と違って，nvidia-docker(-2) を使えるのが利点です。

### USB メモリに Ubuntu のインストーラを作成

Ubuntu の公式ページから，iso をダウンロードし，UNetbootin で USBメモリに Ubuntu のインストーラを焼きました。  
2年くらい前だったので，16.04 にしましたが，いまだったら 18.04 にします。LTR にしたほうが何かといいです。

### Windows のパーティションを小さくする

Windows が入っている SSD に対し，Windows のディスクの管理でボリュームの縮小をして，Win と Ubuntu 半分ずつにしました。  
しかし，一つのドライブに複数の OS を入れるのはおすすめされないようです。  
私もパーティションテーブルがおかしくなり，grub rescue とだけ表示されて OS が見つからなくなる事態に何度かなりました。  
差す場所に余裕があれば，新たに SSD を買ってそちらに Ubuntu に入れるほうがいいようです。

### USB ブートして，インストールする

USB を差した状態で，PC の電源を入れ，ブートメニューを開き（私の PC の場合は，起動時に [F11] キーを連打），メニューから USB を選びます。  
それから画面の案内のとおりに，インストールします。

### GPU のドライバを入れる

### nvidia-docker-2 を入れる

### pix2pix の docker イメージを取得

## 対象地域を決める

標準メッシュ単位だと扱いやすいです。ただし，環境省植生図は TKY の図幅？で少しずれた範囲なので境界付近がカバーされてるか注意してください。  

## 

## 教師データの作成

### 環境省植生図をダウンロード

### 基盤地図情報をダウンロード

#### 道路縁を面にする

### QGIS で色を決める

### QGIS の地図帳機能で細かい図郭で出力

## 