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
# ■ Docker でよく使うコマンド
### コンテナの一覧と起動状態を確認する
```
docker-compose ps
```

### ログを確認する
```
docker-compose logs app
```

### コンテナ内で bash を操作する（コンテナ起動中のみ）
```
docker-compose exec app /bin/bash
```
Docker で困ったら<br>
コンテナがうまく起動しないとき<br>
下記のコマンドでログを確認して、ログに合わせて対応。

### コンテナの起動状態を確認する
```
docker-compose ps
```

### 起動していないコンテナのログを確認する
```
docker-compose logs app
docker-compose logs db
```
対応したらコンテナを起動。

### Docker コンテナの起動
```
docker-compose up -d
```

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

