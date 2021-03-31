# Railsノート

## ざっとした内容

- 新規登録は2つのアクションで構成される。
- 本の感想メモアプリ作成の手順について。

## ステップ1:  newアクション（新規作成画面）

`new`アクションが実行され新規入力画面が表示される、

ここで本のタイトルとメモ本文を入力する。

```
new

/books/new   `GET`
```

create Bookボタンを押すと、画面のない`create`アクションが実行される。

## ステップ2:  createアクション（画面なし）

```
create

/books  `POST`
```

createアクションで一つ前のステップで入力されたタイトルとメモで本のデータを新規登録する。

今からもっと詳しくみていく。

最初は**roots**から！

[![Image from Gyazo](https://i.gyazo.com/cf8fb8adf763aa14ecb595eaf741650a.gif)](https://gyazo.com/cf8fb8adf763aa14ecb595eaf741650a)

今回のリクエストはパスが `/books/new` 、

HTTPメソッドが`GET`なので、

BooksControllerの`new`アクションへ処理が進む。
<br>


次に**コントローラ**をみていく。

ファイルは `app/controllers/books_controller.rb`

```ruby
def new
  @book = Book.new
end
```

newアクションは、 `@book = Book.new`の１行のみ。

`Book.new`でBookクラスの`インスタンス`を作り、`@book`インスタンス変数へ代入し、`ビュー`へ渡す。

Book.newでつくったBookクラスのインスタンスはタイトルとメモを格納できるようになっているが、タイトルとメモのデータは空っぽである。

最後に**ビュー**である。

`views/books/new.html.erb` へ処理が進んでいく。

```ruby
<h1>New Book</h1>

<%= render 'form', book: @book %>

<%= link_to 'Back', books_path %>
```

- renderメソッドは別のビューファイルを埋め込む。
- わざわざ別のファイルに書く理由は、他の画面でもそのファイルを利用することで、同じ部品を共用したいから.
- 埋め込む用のビューファイルを`パーシャル`と言う。

```ruby
<%= render 埋め込みたいファイル名, パーシャル内で使う変数名: 渡す変数 %>
```

＜埋め込むためのルール＞

- renderで書いた文字列の先頭に_を付けたファイル名にする。

（例）

<%= render 'form', book: @book %>だったら、_form.html.erbとする。

パーシャルビュー `_form.html.erb`

```ruby
<%= form_with(model: book, local: true) do |form| %>
  <% if book.errors.any? %>
    <div id="error_explanation">
      <h2><%= pluralize(book.errors.count, "error") %> prohibited this book from being saved:</h2>

      <ul>
        <% book.errors.full_messages.each do |message| %>
          <li><%= message %></li>
        <% end %>
      </ul>
    </div>
  <% end %>

  <div class="field">
    <%= form.label :title %>
    <%= form.text_field :title %>
  </div>

  <div class="field">
    <%= form.label :memo %>
    <%= form.text_area :memo %>
  </div>

  <div class="actions">
    <%= form.submit %>
  </div>
<% end %>
```

2行目にある  <% if book.errors.any? %>はエラーを表示させるコード

[![Image from Gyazo](https://i.gyazo.com/0251048d5639d77dc150fe622e5cca07.gif)](https://gyazo.com/0251048d5639d77dc150fe622e5cca07)

全体としては`form`という名の部品になっている。

formはHTMLでブラウザからサーバへ情報を送信する仕組みである。

## ■ Choromeのデベロッパーツール

- Chromeのデベロッパーツールを使うと、どのようなリクエストがサーバへ送信されたかを見ることができる。
- command+option+iで表示することができる。

## ■ パラメーター

- パラメータとはブラウザから飛んでくるリクエストの中に含まれる情報のこと。
- ユーザーが入力した値が入っている。
- パラメータはparamsで取得できる。

`app/controllers/books_controller.rb`

```ruby
def book_params
  params.require(:book).permit(:title, :memo)
end
```

- `book_params`メソッドはパラメータに関する処理を行っている。

## ■ Strong Parameters

- params以降の`require`, `permi`tメソッドは、パラメータの内容を制限する。
- 意図していないデータが入ってくるのを防ぐための仕組み。
- ここでは、bookのtitle, memoだけを受け取るようにしている。
- `require`には対象となるモデル名（モデルについては次章で説明します）を、

　　`permit`には更新を許可するカラム名を指定します。

- このパラメータを制限する仕組みは`Strong Parameters`と呼ばれている。
- 攻撃に対する防御をしてくれるため、セキュリティ対策として必要。

## まとめ

- 新規入力画面は`new`アクション、新規登録は`create`アクション
- newアクションではまだデータを保存せず、サーバのデータ変更を伴わないためHTTPメソッド`GET`を使う
- createアクションではデータを保存し、サーバのデータ変更を伴うためHTTPメソッド`POST`を使う
- ユーザーがブラウザでformへ入力した内容はリクエスト内のパラメータとしてRailsアプリへ届き、 paramsで渡ってきたパラメータを取得できる
- セキュリティ問題対策のため`StrongParameters`（requireメソッド、permitメソッド）を利用してparamsに制限をかける
