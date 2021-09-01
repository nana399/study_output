# コンテナがうまく起動しないとき
```ruby
# コンテナの起動状態を確認する
docker-compose ps

# 起動していないコンテナのログを確認する
docker-compose logs app
docker-compose logs db
```
対応したらコンテナを起動する。

```ruby
# Docker コンテナの起動
docker-compose up -d

# コンテナの起動状態を確認する
docker-compose ps
```
Dockerfile 周りの対応を行った場合は、イメージから作り直す。

```ruby
# Docker コンテナの停止・削除
docker-compose down

# Docker イメージのビルド
docker-compose build

# Docker コンテナの起動
docker-compose up -d

# コンテナの起動状態を確認する
docker-compose ps
```
上記の対応をしてもコンテナが起動しない場合
Docker 関連のファイルが変更されている可能性があるので、初期の状態に戻す。
```ruby
# dokugaku-engineer/server-side リポジトリをクローンする
git clone https://github.com/dokugaku-engineer/server-side.git

# part 2 のソースコードを任意のディレクトリにコピーする
cp -r sever-side/part2 -t ~/Documents/code

# part2 のディレクトリに移動
cd  ~/Documents/code/part2
```
Docker 関連のファイルを初期状態に戻した上で、src ディレクトリに設置していたファイルを、<br>
`~/Documents/code/part2/src` にコピーして持っていく。

#### それでも起動しない場合
```
1. Docker Desktop を再起動<br>
2. PC を再起動
```
#### ハードディスクの容量が逼迫したら
不要なイメージ、コンテナなどを削除。

```ruby
# Docker の不要なイメージ、コンテナなどを削除する
docker system prune
```

#### ポートが重複して起動しない場合
```
PC を再起動
ポートを使用しているプロセスを調べて kill 
docker-compose.yml の ports の左側のポート番号を変更
```

#### dbコンテナが起動しない場合
下記のエラーでdbコンテナが起動しない場合

```ruby
2017-11-20 02:56:52 1 [ERROR] InnoDB: auto-extending data file ./ibdata1 is of a different size 0 pages
 MB) than specified in the .cnf file: initial 768 pages, max 0 (relevant if non-zero) pages!
2017-11-20 02:56:52 1 [ERROR] InnoDB: Could not open or create the system tablespace. If you tried to a
 to the system tablespace, and it failed here, you should now edit innodb_data_file_path in my.cnf back
and remove the new ibdata files InnoDB created in this failed attempt. InnoDB only wrote those files fu
did not yet use them in any way. But be careful: do not remove old data files which contain your precio
2017-11-20 02:56:52 1 [ERROR] Plugin 'InnoDB' init function returned error.
2017-11-20 02:56:52 1 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
2017-11-20 02:56:52 1 [ERROR] Unknown/unsupported storage engine: InnoDB
2017-11-20 02:56:52 1 [ERROR] Aborting
```
MySQLの古いデータを削除する。

```ruby
# MySQLの以前のデータを削除する
rm -rf docker/db/mysql_data
```

Dockerの不要なイメージ、コンテナ、ネットワーク、ボリュームを削除。

```ruby
# Docker コンテナの停止・削除
docker-compose down

# Docker の不要なイメージ、コンテナ、ネットワーク、ボリュームを削除する
docker system prune --volumes
```

MySQLのデータの同期をやめるために、 `docker-compose.yml` の下記3行目を削除する

```ruby
db:
  volumes:
    - ./docker/db/mysql_data:/var/lib/mysql # ← この行を削除
    ```
イメージから作成し直す。
```ruby
# Docker イメージのビルド
docker-compose build

# Docker コンテナの起動
docker-compose up -d

# コンテナの起動状態を確認する
docker-compose ps
```
