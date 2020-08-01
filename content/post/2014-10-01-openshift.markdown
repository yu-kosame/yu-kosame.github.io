---
title: "OpenShift にさわってみた"
date: "2014-10-01"
categories: ["others"]
slug: openshift
---
<!--more-->
## アカウント登録
OpenShift online に登録しました。  
その過程で，メールの URL から認証するところでなぜかエラーになりましたが，次の日アクセスするとうまくできました。  

## アプリ登録
Django を選択し，その後いろいろ設定します。  

```
Public URL  : [appname]-[domainname].rhcloud.com  
Source Code : git:/github.com/openshift/django-example.git  
Cartridges  : Python 2.7  
Scaling     : No scaling  
Region      : No preference  
[Create Application]
```

## ページの確認
admin へのリンクに進むと，もうデプロイできてる…！

## 公開鍵の登録
mac の場合，

```bash
ssh-keygen
vim /Users/username/.ssh/id_rsa.pub
```
OpenShift の"Set an SSH key" にコピペする。

参考：
[Mac OS X でSSH公開鍵を作成する - マークアッパーなアタシのための雑記](http://d.hatena.ne.jp/uco_twinkle/20080409/1207703829)

## クライアントツールをインストールする
mac の場合（自分memo）

9. Ruby はインストール済み
9. git もインストール済み
9. ```sudo gem install rhc```
9. ```rhc setup```

```bash
Login to openshift.redhat.com: ***@***com # アカウント名
Password: ***

Generate a token now? (yes|no) yes

Your public SSH key must be uploaded to the OpenShift server to access code.  Upload now? (yes|no) yes # さっきコピペしたんだけどな…

Your client tools are now configured.
```

参考：
[Installing Client Tools | OpenShift Developers](https://developers.openshift.com/en/getting-started-client-tools.html)

## アプリの編集
web インターフェイスの Eclipse plugin もあるけど，コマンドラインのほうがおすすめらしい。  
公式ドキュメントにはコマンドラインでのアプリ作成方法が載ってますが，web 画面で作ったのでとばす。

### ローカルにコピー
コマンドラインからつくると，Git Repository が自動的にローカルに保存してくれるらしいですが，web の人は，アプリのページの "Source Code" の URL をコピーして，
```bash
git clone ssh:/.../ /Users/***/appname
```
などとします。

こうやって，ローカルで編集するということですね。

### git を使い始める
```bash
cd /Users/***/appname
git init
```

### （変更後）再投稿する
```bash
git add .
git commit -m "some title"
git push
```

ローカルに落としたフォルダ内の README.md をみると，```git push``` の後，django admin のユーザ名とパスワードが流れるから気をつけろと書いてある。  
なので，よーく探したけど，見つからなかった…。

調べてみるとエラーらしく，[How to login on the admin painel? | OpenShift Forums](https://forums.openshift.com/how-to-login-on-the-admin-painel) に
	Django has a standard command to solve this problem:	
		1. Login using ssh
		2. Goto the repo/wsgi/openshift directory
		3. type: ./manage.py createsuperuser (and follow instructions)
とあったので，
```bash
ssh 128d6...@appname-domainname.rhcroud.com
cd app-root/repo/wsgi/openshift
.manage.py createsuperuser
```
と，しました。

これで，admin ページに入れました。

## 参考
- [OpenshiftでDjango | Workpiles](http://workpiles.com/2014/06/openshift-django-web/)

