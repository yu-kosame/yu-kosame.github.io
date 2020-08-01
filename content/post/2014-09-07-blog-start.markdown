+++
title = "blog start"
date = "2014-09-07T22:59:00+09:00"
categories = ["others"]
draft = false
+++
<!--more-->
## Crotal を始めた
```bash
pip install crotal
cd /home/user/                                   # ソースを置くディレクトリに移動
crotal init sitename                             # 新しいサイトの作成
cd sitename/
crotal generate sitename 
crotal server                                    # localhost:8000でプレビュー
crotal new_post 'blog start'                     # 新しい投稿
vim source/posts/2014-09-07-blog-start.markdown  # 投稿の編集
```
## Crotal のデプロイ
```bash
crotal generate -f
rsync -r _sites/ /var/www/crotal  # 公開用サーバで編集してるので crotal deploy は使わない
```
```bash
# httpd.conf l.292
DocumentRoot "/var/www/crotal"
```
```bash
apachectl restart
```
## Crotal の設定・調整
```bash
vim _config.yml  # いろいろ
```
iPhoneで見ると幅が少し広いらしく，ふよふよするので変更する
```bash
# themes/default/static/css/style.css
.container { width: 320px; }  # l.295 350px -> 320px

.left-area { width: 320px; }  # l.300 350px -> 320px
```
段落 p の下の行間がやや広いので変更する
```bash
# themes/default/static/css/style.css
.entry p {font-size: 18px; margin-top: 0.25em; line-height: 1.25; }  # l.146
```
見出しの下の行間がやや広いので変更する
```bash
# themes/default/static/css/style.css
h1, h2, h3, h4, h5, h6 { margin-bottom: 0.25em; color: \#111; line-height: 1em; font-weight: normal; }  # 1em -> 0.25em
```
