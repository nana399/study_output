## ■ Gemライブラリ

- いろいろなプログラムで共通して使える便利な公開されたプログラムをライブラリと呼ぶ。
- Rubyの世界にもライブラリがあり、Gemと呼ばれている。
- Gemは [rubygems.org](http://rubygems.org/) で公開されている。

## ■ Gemのインストール

- Gemをインストールするにはgem iコマンドを利用
- gem iのiはinstallの略。

```ruby
gem i awesome_print
```

↓ダウンロード後（ターミナル）

```ruby
Fetching awesome_print-1.9.2.gem
Successfully installed awesome_print-1.9.2
Parsing documentation for awesome_print-1.9.2
Installing ri documentation for awesome_print-1.9.2
Done installing documentation for awesome_print after 0 seconds
1 gem installed
```

## ■ Bundlerの存在

- Gemの管理をかんたんにする`Bundler`という仕組みが用意されている。

## ■ Gemのバージョンアップ

- 各Gemは随時、新しいバージョンがリリースされる。
- `Gemfile`に書かれたGemの新しいバージョンをインストールしたい場合は`bundle update`コマンドを使う。
- 特定のGemだけをバージョンアップしたい場合は、`bundle update Gem名` と`Gem名`をつけて実行

## ■ **まとめ**

- いろんなプログラムから使える便利な公開されたプログラムを`ライブラリ`と呼ぶ
- GemはRubyの世界のライブラリ
- Gemをインストールするには`gem i`コマンド（gem installの省略形）を使う
- `Bundler`は複数のGemをかんたんに管理する仕組み
- BundlerではGemfileという名前のファイルに使用するGemを書く
- Gemfileを作成し`bundle install`コマンドを実行すると、Gem群がインストールされる
- bundle installコマンドを実行するとGemfileをもとにGemfile.lockファイルが生成されるので、両方をソース管理対象にする
- Gemfileは発注書、Gemfile.lockは納品書に相当する
- 
- `carrierwave gem`を使うと画像アップロード機能を追加できる
- Gemfileに新しいgemを追加した後、`bundle install`コマンドでインストールする
- マイグレーションファイルの生成は`rails g migration Addカラム名Toテーブル名 カラム名:型名`
