# Docker WordPress Base

## 概要

WordPressに必要なミドルウェア等をdockerを使って一括で構築できます。

コンテナ起動後、``app/``フォルダ以下にWordPressのファイルが展開されるので、別プロジェクト管理したい場合は適宜フォークや切り出し管理して下さい。

### 準備

__1. dockerをインストール__

下記URLから自分の環境に合わせてDLしてインストールしアプリを起動

[[Mac版](https://download.docker.com/mac/stable/Docker.dmg)]

[[Windows 10 Professional or Enterprise 64-bit版](https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe)]

[[上記以外のWindowsマシン](https://download.docker.com/win/stable/DockerToolbox.exe)]

``terminal``や``PowerShell``,``GitBash``等で、以下コマンド実行、インストールされているか確認。

```
$ docker --help
$ docker-compose --help
```

__2. 設定ファイルを用意__

ルートディレクトリ直下の``variables.env.sample``をコピー
``variables.env``にリネームして配置。

以下、``variables.env.sample``の記載内容(説明付き)
任意の値に変更して下さい。

```
# MySQL settings
MYSQL_ROOT_PASSWORD=mysqlpwd # MySQLのRootパス
MYSQL_DATABASE=wordpress # 初期に作成するスキーマ
MYSQL_USER=wordpress # 一般ユーザー
MYSQL_PASSWORD=wordpresspass # 一般ユーザーパス名

# WordPress settings
WORDPRESS_DB_NAME=wordpress # WordPressで利用するスキーマ名
WORDPRESS_DB_USER=wordpress # WordPressで利用するMySQLユーザー
WORDPRESS_DB_PASSWORD=wordpresspass # WordPressで利用するMySQLユーザーのパス
```

## 起動方法等

以下、全てディレクトリ直下での作業。

__コンテナ起動__

サービス起動

```
# ctl+cで終了
$ docker-compose up
```

バックグランド起動

```
$ docker-compose up -d
# stopは
$ docker-compose stop
```

__コンテナ削除__

```
$ docker-compose down
```

__アクセス方法__

```
http://localhost:8011
```

## データベース情報

* HOST ``127.0.0.1``
* PORT ``33306``
* ROOT_PASS ``mysqlpwd``

``variables.env.sample``の設定により変わります。

## 初期化したい時

``app/``と``data/``直下のデータを削除し、コンテナ削除、コンテナ起動をすると新たにデータが配置されます。

## 備考

* WordPress本体データ一式は``app/``フォルダ直下に配置されます。
* databaseの情報は``data/db-data/``フォルダ直下に配置されます。

## Changelog

### 20171206

WordPress4.9から4.9.1へ

### 20171121

WordPress4.8.3から4.9へ

### 20171114

初版

