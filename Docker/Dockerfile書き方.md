# Dockerファイル
srcディレクトリと同じ場所にDockerfileを作る

## 書き方
```ruby
FROM ruby:2.7　#バージョンを指定する

WORKDIR /var/www

COPY .src/var/www #アプリケーションコードをDockerにコピーする

CMD　["/bin/bash"] #cmdはコマンド、/bin/bashでシェルを起動できる
```

```ruby
$docker image build -t sample⬅なにか記述抜けたかも
$docker container run -it　-p 4567:4567 --name コンテナ名 -v ${pwd}/src:/var/www　sample/sinatra:latest
```
-itオプションはinteractive（相互利用）オプション<br>
-pはポート番号指定<br>
-vはボリュームのオプション、こうすることでソースコードがDockerに共有される、-vをしないとimageを毎回共有する必要があり面倒であるため。
