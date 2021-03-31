# Railsノート

## ■ rails new コマンドでやっていること

- Railsアプリとして動作するのに必要なファイルとフォルダの作成
- 利用するGemライブラリ（Rubyの便利なプログラム集）をダウンロードして利用可能に
- rails webpacker:install, yarn installが実行されて、JavaScriptのライブラリをダウンロードして利用可能に

## ■ タイムゾーンの設定

`config/application.rb`ファイル中に `config.time_zone = 'Asia/Tokyo'` と設定する。この方法の利点は、プログラムの中のあちこちで in_time_zone('Asia/Tokyo') を書かずに済み、config/application.rbファイルの1カ所にまとめることができる。

## ■ Webアプリの仕組み

Webサーバ上で動作しているWebアプリはリクエストを受け取ると、「レスポンス」としてHTMLで書かれたテキストを作ってブラウザへ返す。ブラウザはHTMLを解釈して、私たちにとって見やすい、いつも見慣れたWebページを表示する。

HTMLはHyperText Markup Languageのことで、Webページを記述するための言語である。

[![Image from Gyazo](https://i.gyazo.com/ecd177025e12c4ae8847ad01a35fd1b5.gif)](https://gyazo.com/ecd177025e12c4ae8847ad01a35fd1b5)

## ■ Webサーバーとは

Webサーバーは「Webサービスを提供する場合に必要な共通の機能を提供するもの」

## ■ **Railsアプリの動作まとめ**

今回つくったRailsアプリの動作を図にすると次のようになる。

![https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/21359/b011613d-0bda-4328-80b3-95a9d02fdcaa.png](https://techpit-market-prod.s3.amazonaws.com/uploads/part_attachment/file/21359/b011613d-0bda-4328-80b3-95a9d02fdcaa.png)

ブラウザのURL欄にアドレスを入力してEnterを押すとリクエストが飛ぶ。リクエストを受け取ったRailsアプリはHTMLをつくり、レスポンスとして返す。レスポンスを受け取ったブラウザはHTMLを解釈し、画面に表示する。

## ■ **Railsでの開発の進め方**

Railsでの基本的な開発の進め方は以下の2つを繰り返すサイクルになる。

- ひな形になるファイル（ソースコードや設定ファイル）の生成
- つくっているアプリ用にファイルを変更、追記

## Rails newで作られるファイル

[![Image from Gyazo](https://i.gyazo.com/2b9768a7413692108f2e9191ee4c780a.gif)](https://gyazo.com/2b9768a7413692108f2e9191ee4c780a)

## ■ リクエストからレスポンスまでの流れ

リクエスト → Routes → Controller → View →レ スポンス

[![Image from Gyazo](https://i.gyazo.com/a3bc1abe14d660bd215ad0ee7f98190e.gif)](https://gyazo.com/a3bc1abe14d660bd215ad0ee7f98190e)

リクエストを受けたRailsアプリは、Routes, Controller, Viewの3つのコードを通過してそれぞれの場所で処理を行い、レスポンスとしてHTMLを生成して返す。

## ■ Routesの役割

Routesは「リクエストのURLとHTTPメソッド」に応じて次に処理を行う先を決める役割を担っている。Routesの処理が終わると、コントローラのアクションへ処理が移る。RoutesはリクエストとControllerのアクションの対応表の存在。

```
- URL

    インターネット上の住所のこと。アクセス先を指定するもの。

- HTTPメソッド
    - そのURLに対して「何をするか」を指示するもの。
    - HTTPメソッド”GET"でリクエストが飛ぶ。
    - GETは「ページを取得する」指示のこと。
```

[![Image from Gyazo](https://i.gyazo.com/0b842ef614c5adc194a291e8f35b233b.gif)](https://gyazo.com/0b842ef614c5adc194a291e8f35b233b)

```
今回リクエストされたもので考えると、

URL：http://localhost:3000/hello/index

HTTPメソッド：`GET`

　　　　　↓

これらのリクエストにより、

HelloControllerの`index`アクションが呼ばれる
```

## ■ コントローラ

- コントローラでは様々な処理を行い、次のビューで使うデータを作って渡す。
- 次の処理先となるビューではコントローラで指定することは出来ないが、指定していないときは、コントローラおよびアクションと同名のビューを選択する。

## ■ インスタンス変数とは

- @始まりの変数
- インスタンス変数を使うと、コントローラからこのあとの処理先であるビューへ情報を伝えることができる。
- @始まりでは無い変数はローカル変数と呼ばれる。

## ■ ビュー

- ビューではHTMLなど、ユーザーに届く部分を作る
- 作られたHTMLはレスポンスとしてブラウザへ送られる。
- `index.html.erb`は、HTMLのもとになるファイル。
- `<%`= と` %>` というタグは、Rubyのコードを実行するためのタグ

## ■ ここまでのまとめ

- Routes→コントローラ→ビューの順番で処理を行い、HTMLを作ってブラウザへレスポンスを返す
- RoutesはリクエストのURLとHTTPメソッドに応じて、処理をするコントローラとアクションを決める対応表
- コントローラはさまざまな処理を行い、ビューでつかう情報を@はじまりのインスタンス変数を使って渡す
- ビューはテンプレート書かれたRubyのコードを実行して埋め込み、HTMLを作る

## ■➕α（公式ドキュメント）

- [Rails ガイド: Rails のルーティング](https://railsguides.jp/routing.html)

→Routesについての詳しい説明

- [Rails ガイド: Action Controller の概要](https://railsguides.jp/action_controller_overview.html)

→コントローラについての詳しい説明

- [Rails ガイド: Action View の概要](https://railsguides.jp/action_view_overview.html)

→ビューについての詳しい説明

- [Rails ガイド: レイアウトとレンダリング](https://railsguides.jp/layouts_and_rendering.html)

→コントローラから次のビューを指定する方法や、ビューを整理して書くための情報などが説明されている

## 参考


[Railsの教科書](https://tatsu-zine.com/books/rails-textbook)
