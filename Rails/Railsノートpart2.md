# Railsノート

## ■CRUDの基礎

Webアプリの基本となる４つの機能

- Create：ページの新規作成
- Read：表示
- Update：更新
- Destroy：削除

これらの頭文字をとってCRUDと呼ばれている。

## ■ scaffoleコマンド

- rails g scaffoldコマンドは、新規作成、表示、更新、削除、各機能を一度に作る機能
- つまりこのコマンド使うことでCRUDが一気に作れちゃうよーっていうやつ
- scaffoldは英語で「（建築現場などの）足場」という意味

画面あり

- index ・・・`GET`
- edit・・・ `GET`
- new ・・・`GET`
- show・・・ `GET`

画面なし

- destroy ・・・`DELETE`
- update ・・・`PATCH or PUT`
- creaete・・・ `POST`

## ■ indexアクション

- indexアクションでデータの一覧をみることができる。

今から、

routes→Controller→Viewの順の流れでみていく。

▶  Routes

Routes表から、リクエストごとに次に処理するコントローラとアクションが決まる。

[![Image from Gyazo](https://i.gyazo.com/1dbc5edb90952d555bd029c95ade2733.gif)](https://gyazo.com/1dbc5edb90952d555bd029c95ade2733)

今回はURLが"`/books`"、

HTTPメソッドが "`GET`"であるため、

「/booksにGETでアクセスされたとき、

`BooksController`の`index`アクションへ処理を渡す」という意味になる。

よって、次に進むべきコントローラは`books#index`（BooksControllerのindexアクション）となる。

## コントローラ

```ruby
class BooksController < ApplicationController
...
def index
@books = Book.all
end
...
```

このファイルでやっていることは、この`@books = Book.all`のみ。

Book.allで全データを取得し、`@books`インスタンス変数へ代入する。

`@books`と複数形になっているのは、`Book.all`で取得するデータが複数の本のデータを格納していることを示すため。

次はビューファイルへ処理が移る。

## ビュー

- ビューでレスポンスとして返されるHTMLが作られる。
- 我々が見る画面の部分

ファイル `app/views/books/index.html.erb`

```ruby
erb
<% @books.each do |book| %> ⬅️ @booksはbookがいくつか入った配列
  <tr>
    <td><%= book.title %></td> ⬅️初回のbook.title "RubyとRailsの学習ガイド" 
    <td><%= book.memo %></td> ⬅️初回のbook.memo "Rails関連技術地図とそれらの学習資料の紹介"
    <td><%= link_to 'Show', book %></td>
    <td><%= link_to 'Edit', edit_book_path(book) %></td>
    <td><%= link_to 'Destroy', book, method: :delete, data: { confirm: 'Are you sure?' } %></td>
  </tr>
<% end %>
```

`<%`= `%>`で囲まれた部分は、Rubyコードの実行結果がHTMLとして埋め込まれる。
