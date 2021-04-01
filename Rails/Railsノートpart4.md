# Railsノート

## ■ モデル

- データを保存する仕組み

## データの永続化とは
- 永続化とは、[https://e-words.jp/w/永続性.html](https://e-words.jp/w/%E6%B0%B8%E7%B6%9A%E6%80%A7.html)
- 変数の有効範囲をスコープという。

      

        `app/controllers/books_controller.rb`

        ```ruby
        def create
          @book = Book.new(book_params) # ⬅️BookクラスはModelという種族に属する
          respond_to do |format|
            if @book.save # ⬅️ここで保存
              format.html { redirect_to @book, notice: 'Book was successfully created.' }
              format.json { render :show, status: :created, location: @book }
            else
              format.html { render :new }
              format.json { render json: @book.errors, status: :unprocessable_entity }
            end
          end
        end
        ```


- このコードでモデルを利用している部分は、
-  `if @book.save`  この部分。
-  ここでコードを保存している。


## ■ モデルの基本的な使い方その1　保存

- 以下の手順でデータを保存することができる。

        ```ruby
        book = Book.new(title: "RubyとRailsの学習ガイド", memo: "Rails関連技術地図とそれらの学習資料の紹介")
        book.save!
        ```

        - モデル名（モデルのクラス名）は英語の単数形、大文字始まりにするルールがある。
        - `Book`がモデル名、小文字の`book`は変数名である。
        - 1つのBookモデルオブジェクトが代入されるため単数形を使う。

        - Bookモデルオブジェクトの`save!`メソッドを呼び出すと保存できる。
        - 存するメソッドはいくつかあり、他にもsave, create!, createメソッドなどがある。
        - saveとsave!の違いは、保存に失敗したとき、saveメソッドはfalseを返し、save!メソッドでは例外が投げられる。

## ■ モデルの基本的な使い方その2　読み込み

        ```ruby
        books = Book.all.to_a
        ```

- `Book.all`で保存されているBookモデルの全データを取得できる。
- `Book.all.to_a`でArray（配列）にBookオブジェクトが詰まって返ってくる。
- `to_a`はArrayオブジェクトへ変換するメソッド
- 代入される変数名は小文字の`books`で、複数の`Book`オブジェクトが代入されるので複数形を使う。

## モデルの基本的な使い方その3　検索

        ```ruby
        book = Book.where(title: "RubyとRailsの学習ガイド").first
        book.title #=> "RubyとRailsの学習ガイド"
        book.memo #=> "Rails関連技術地図とそれらの学習資料の紹介"
        ```

- whereメソッドを使うと検索ができる。
- タイトルが"RubyとRailsの学習ガイド"であるBookオブジェクトが返る。
- 検索結果が複数になることもあるので、firstメソッドで最初の1つを取得している。
- 取得するオブジェクトは1つなので、それを代入する変数名bookは単数形になっている。
- 取得したBookオブジェクトはtitleメソッドでタイトルを、memoメソッドでメモをそれぞれ返す。

## ■ モデルの仕組み

- モデルのコードはapp/models/フォルダ以下にある。

        `app/models/book.rb`

        ```ruby
        class Book < ApplicationRecord
        end
        ```

- Bookモデルにはコードがほとんどない。

## 問: saveやallといったメソッドが使えるのはなぜか？

→　答えは `ApplicationRecord` クラスを継承しているから。 `ApplicationRecord` クラス（およびさらに親のクラス）がモデルの仕事に必要な機能を持っている。それを継承している`Book`クラスも同じ機能を持つ。

## 問: titleやmemoといった要素があることをどこで知るか？

- →答えは「`データベース`（DB）から。
- ApplicationRecordは`データベース`から情報を得て、Bookモデルにtitle、memoという要素があることを知っている。
- その情報を使って、book.titleやbook.memoといったメソッドを提供している。

## ■ データベース（DB）とは

- DBとは、データを保存したり、読み出したり、検索したりするために特化したプログラム
- DBへアクセスするには一般に専用の言語（SQL）を用いるため、Rubyのコードからは扱いづらいという問題がある。
- モデルはDBを便利につかうための仕組みでもあり、RubyでDBを容易に扱うことができる機能も提供している。

   
- つまり、モデルが簡単にDBにアクセスできる機能を提供し、プログラマはモデルを通じてDBとデータのやり取りを行っている。

## ■ DBはいつ作られたのか？

        ```ruby
        $ rails g scaffold book title:string memo:text
        $ rails db:migrate
        ```

- books appを作る一連のコマンドを入力した際にDB程度を作成していた。
 - `scaffold`コマンドはいろいろなものを作りますが、その1つとしてDBの設計書「`マイグレーション（migration）ファイル`」をつくります。

- `rails db:migrate`コマンドを実行すると、さきほど作られた設計書を使ってDBを作る。

## ■ マイグレーション（migration）ファイル

- DBの設計書をマイグレーションファイルと呼ぶ。
- ファイル名は実行した日付から作られた数字が入っている。
- rails gコマンドを実行するごとに異なるファイル名になる。

`db/migrate/20191008234834_create_books..rb`

        ```ruby
        class CreateBooks < ActiveRecord::Migration[6.0]
          def change
            create_table :books do |t|
              t.string :title
              t.text :memo

              t.timestamps
            end
          end
        end
        ```

#### ■１行目 `ActiveRecord::Migration[6.0]`

- `ActiveRecord::Migration[6.0]` の末尾にある数字はRailsのバージョンを表している。Rails6.0.xではこのように6.0となる。


#### ■３行目  `create_table :book`
- booksという名前のテーブルを作る。
- DBはテーブルという単位でデータを管理する。
- ここでは、本に関するデータを保存するためにbooksという名前のテーブルを作っている。
- テーブル名
- はモデル名の複数形にするというルールがある。

#### ■４行目 `t.string :title` と5行目 `t.text :memo`
- テーブルの要素を作成する。
- booksテーブルにはtitleという要素とmemoという要素を持つ。
- この要素のことをカラムと呼ぶ。

#### ■t.timestamps
- created_at（作成日時）、updated_at（更新日時）を記録するカラムを作る。

- DBテーブルはExcelとよく似たもの。
- DBへデータを格納していくことは、title、memoといった列があるExcelのシートに1行ずつデータを格納していくイメージ。

       

- DB設計書（migration）からDBテーブルを作るのが `rails db:migrate` コマンド
- `rails db:migrate`コマンドを実行すると、/db/migrateフォルダにあるマイグレーションファイルを実行してDBテーブルを作る。

## ■ 保存したあとの処理

- @book.saveは成功するとtrue、失敗するとfalseを返す。

        ```ruby
        @book = Book.new(book_params)
        if @book.save
          redirect_to @book, notice: 'Book was successfully created.'
        else
          render :new
        end
        ```

#### ＜成功バージョン＞

- `redirect_to @book, notice: 'Book was successfully created.'`が実行される。
- `redirect_to`はリダイレクト（新たにリクエストを発行して画面遷移させる）指示で、ここでは`show`アクションへのリクエストが発生する。
- 保存した本の詳細ページ（BooksControllerのshowアクション）が表示される。
- 後ろのnotice部は画面に表示させる文を設定している。

#### ＜失敗バージョン＞

- `render :new`が実行される。
- renderはコントローラの次の処理である`ビュー`を指定する。
- ここでは`app/views/books/new.html.erb`がビューとして使われ、新規入力画面、つまり直前で入力していたページが表示される。

## ■ まとめ

- DBはデータの保存、読み込み、検索に特化したプログラム
- モデルはDBを便利に使うための道具。DBとモデルはセットで使われる
- マイグレーション（migration）ファイルはDBを作るための設計書
- rails db:migrateはマイグレーションファイルからDBを作るコマンド

 ## Rails Guide

 - [Rails ガイド: Active Record の基礎](https://railsguides.jp/active_record_basics.html)
           
- [Rails ガイド: Active Record マイグレーション](https://railsguides.jp/active_record_migrations.html)
           
- [Rails ガイド: Active Record クエリインターフェイス](https://railsguides.jp/active_record_querying.html)
            
- [Rails ガイド: Active Record バリデーション](https://railsguides.jp/active_record_validations.html)
      
- [Rails ガイド: Active Record の関連付け](https://railsguides.jp/association_basics.html)
            



## ■ 既存のDBテーブルにカラムを増やす

        ```ruby
        $ rails g migration Addカラム名Toテーブル名 カラム名:型名
        ```

        - こうすることで新しいカラムを追加しmigrationファイルを作ることができる。
        - 過去に作ったmigrationファイルを変更することはできないため、新しいmigrationファイルを作らなければいけない。

        ### migrationファイルを作成したら、rails db:migrateコマンドでDBへ内容を反映させる

        ```ruby
        $ rails db:migrate
        ```

## ■ 新しいモデルとmigrationを同時に作成する

        - `rails g`コマンドにmodelを指定するとmodelとmigrationを生成できる。

        ```ruby
        rails g model book title:string memo:text
        ```
