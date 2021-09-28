# ■ 環境構築
### Docker イメージのビルド
```
docker-compose build　
```

### Docker コンテナの起動
```
docker-compose up -d
```
### Dockerコンテナの作成と起動
```
run -p 8000:8000 --name webrick sample/webrick:latest
```
- -pはローカルのポートの指定をしている
- ローカルの8000番ポートをDockerの8000番ポートに接続させている

### Docker コンテナ内でコマンドを実行する
```
docker-compose exec app php -v
```

### Docker コンテナの停止・削除
```
docker-compose down
```

### Docker　コンテナの起動
```
docker-compose up
```
→これをすると全部のファイルを起動する
# ■ Docker でよく使うコマンド
### コンソール開いておいてその中でコマンド操作
```
docker-compose run app bash
```



### ログを確認する
```
docker-compose logs app
```
appの部分はファイル名を書く<br>
正確にはコンテナ名

### コンテナ内で bash を操作する（コンテナ起動中のみ）
```
docker-compose exec app /bin/bash
```
Docker で困ったら<br>
コンテナがうまく起動しないとき<br>
下記のコマンドでログを確認して、ログに合わせて対応。

### コンテナの一覧を表示する
```
docker-compose ps
```
コンテナの一覧を表示する

### 起動していないコンテナのログを確認する
```
docker-compose logs app
docker-compose logs db
```
対応したらコンテナを起動。


### コンテナの起動状態を確認する
```
docker-compose ps
```
Dockerfile 周りの対応を行った場合は、イメージから作り直す。

### Docker コンテナの停止・削除
```
docker-compose down
```

### Docker イメージのビルド
```
docker-compose build
```

### Docker コンテナの起動
```
docker-compose up -d
```

### コンテナの起動状態を確認する
```
docker-compose ps
```

### コンテナを作成してコマンド実行
```
docker-compose run ＜サービス＞＜コマンド＞
```
### 起動中のコンテナにコマンド実行

```
docker conatainer exec ＜サービス＞　＜コマンド＞
```
コマンド例　ruby -v
### 使っていないimageのお掃除をしてくれる
```
Docker system prune -a
```
-aは全てのというオプション<br>
個別で消すと時間がかかる

## Docker環境でのrailsのルーティング確認方法
```
docker-compose run web bundle exec rake routes
```

マイグレーションのやり直し
```
$ docker-compose run app bundle exec rails db:migrate:reset
```

