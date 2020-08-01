---
title: "サブドメインをつくる"
date: "2014-09-30"
categories: server
slug: sub_domain
---
## DNS にサブドメインを登録
お名前.com の場合です。

9. お名前.com ドメインNavi
9. ネームサーバーの設定 -> DNS関連機能の設定
9. DNSレコード設定を利用する
9. 「ホスト名 : sub, TYPE : A, TTL : 3600, VALUE : xxx.xxx.xxx.xxx, 状態 : 有効」で追加

## apache の設定

```bash
# /etc/httpd/conf.d/virtualhost.conf
NameVirtualHost *:80

<virtualHost *:80>
    ServerName ***.jp
    DocumentRoot /var/www/html
</virtualHost>

<virtualHost *:80>
    ServerName sub.***.jp
    DocumentRoot /var/www/sub
</virtualHost>
```

```
apachectl restart
```

## 

参考：

- [さくらVPSでサブドメインを追加してみた | MAMANのITブログ](http://mamansoft.net/blog/さくらVPSでサブドメインを追加してみた/)
- [iTIPS集:Webサーバ(Apache)　『バーチャルホストの公開方法』 - はじめての自宅サーバ構築[kajuhome.com]](http://kajuhome.com/tips/tips_03_004.shtml)

