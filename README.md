## これは何？

サクッと使えるLAMP環境のdocker-compose一式です。  
本番運用は想定しておりません。あくまでサクッと使えるテスト用環境です。


## 環境情報

- CentOS 8
- Apache
- PHP 7.4
- MySQL 8


## 使い方

### 共通項目

- 設定系はすべて`[data]`フォルダ配下に入っています
- htdocsフォルダ配下にパスが通っていますので、**htdocsフォルダにPHPなどのファイルを置いて**いきます
    - パスを変更したい場合は、`[apache] > [conf.d] > userdir.conf`ファイルの`/var/www/html/`の部分を変更してください。

#### コマンド類

```bash
# 初回起動 or コンテナのビルド
docker-compose up -d --build

# 起動
docker-compose up -d

# 停止
docker-compose down

# apacheのコンテナにアクセス
docker-compose exec apache bash

# phpfpmのコンテナにアクセス
docker-compose exec phpfpm bash

# mysqlのコンテナにアクセス
docker-compose exec mysql bash
```

### Windows 10 Home

- docker tool boxを想定
- アクセスは `http://192.168.99.102:8080/` のような感じ
    - `docker-machine ip`で表示されるIP + Port8080で繋がります
- docker tool boxは、git及びvirtual boxを別々にインストールしましょう。docker tool box内包のgitなどだとエラーで起動できませんでした。


### Windows 10 Pro

未実証


### Linux 

未実証

### Mac

未実証


## 謝辞

- mysqlのコンフィグファイル（my.conf）は以下の記事のものを利用させていただきました
    - [docker-compose MySQL8.0 のDBコンテナを作成する](https://qiita.com/ucan-lab/items/b094dbfc12ac1cbee8cb)

