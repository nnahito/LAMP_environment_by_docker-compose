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
- MySQLへの接続情報
    - host: `mysql`
    - ユーザ名: `root`
    - パスワード: `root`
    - デフォルトで作られる空DB: `docker`

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

- docker for windowsで起動確認
- volumesマウント系で少し手こずったので、注意
    - [Docker for Windowsで快適な環境を得るまでの そこそこ長い闘い](https://qiita.com/YukiMiyatake/items/73c7d6c4f2c9739ebe60)
    - [Windows10でESET＋Laradocのセットアップ時にエラー「Drive sharing seems blocked by a firewall」が出た場合の対処。](https://mrkmyki.com/2018/11/24/windows10%E3%81%A7eset%EF%BC%8Blaradoc%E3%81%AE%E3%82%BB%E3%83%83%E3%83%88%E3%82%A2%E3%83%83%E3%83%97%E6%99%82%E3%81%AB%E3%82%A8%E3%83%A9%E3%83%BC%E3%80%8Cdrive-sharing-seems-blocked-by-a-firewall/)
    - [Windows10 × Docker for Windows トラブルシューティング](https://qiita.com/takeru08ma/items/7878a293c55a9902f404)


### Linux 

未実証

### Mac

未実証


## 謝辞

- mysqlのコンフィグファイル（my.conf）は以下の記事のものを利用させていただきました
    - [docker-compose MySQL8.0 のDBコンテナを作成する](https://qiita.com/ucan-lab/items/b094dbfc12ac1cbee8cb)

