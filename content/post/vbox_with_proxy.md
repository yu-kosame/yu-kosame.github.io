+++
draft = false
date = "2017-07-04T21:02:13+09:00"
categories = ["windows", "linux"]
slug = ""
title = "プロキシ下で VirtualBox の ゲストの Ubuntu に ssh する"

+++

## vbox の環境設定

![](/pict/vbox_with_proxy/ubu1604_vbox_1.png)

![](/pict/vbox_with_proxy/ubu1604_vbox_2.png)

![](/pict/vbox_with_proxy/ubu1604_vbox_3.0.png)

![](/pict/vbox_with_proxy/ubu1604_vbox_4.png)

![](/pict/vbox_with_proxy/ubu1604_vbox_5.png)

![](/pict/vbox_with_proxy/ubu1604_vbox_6.png)

![](/pict/vbox_with_proxy/ubu1604_vbox_3.1.png)

## Windows のネットワーク接続の設定
コンパネ -> ネットワークと共有センター -> アダプターの設定の変更

![](/pict/vbox_with_proxy/ubu1604_vbox_7.png)

![](/pict/vbox_with_proxy/ubu1604_vbox_8.png)

![](/pict/vbox_with_proxy/ubu1604_vbox_9.png)

## ヴァーチャルマシンの設定

![](/pict/vbox_with_proxy/ubu1604_vbox_10.png)

![](/pict/vbox_with_proxy/ubu1604_vbox_11.png)

![](/pict/vbox_with_proxy/ubu1604_vbox_12.png)

## ゲストの Ubuntu での設定

ゲストOS は Ubuntu 16.04 です。

### /etc/network/interfaces
```
source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp0s3
iface enp0s3 inet dhcp

# Nat
auto enp0s8
iface enp0s8 inet dhcp
```
![](/pict/vbox_with_proxy/ubu1604_vbox_13.png)
### プロキシの設定
#### bash
```
export http_proxy=http://xxx.xxx.xxx.xxx:port
export https_proxy=http://xxx.xxx.xxx.xxx:port
export ftp_proxy=http://xxx.xxx.xxx.xxx:port
```

#### /etc/apt/apt.conf
```
Acquire::http::proxy "http://xxx.xxx.xxx.xxx:port";
Acquire::https::proxy "http://xxx.xxx.xxx.xxx:port";
Acquire::ftp::proxy "http://xxx.xxx.xxx.xxx:port";
```

## tera term での ssh 接続
![](/pict/vbox_with_proxy/ubu1604_vbox_16.png)


