# Railsのアプリ設計

## ActiveRecordの命名ルール

・モデルのクラス- 単数形、語頭を大文字にする（例：BookClub）

・データベースのテーブル - 複数形、語はアンダースコアで区切られる（例：book_clubs）

## ActicveRecordのスキーマルール

- 外部キー

    ・テーブル名の単数形_idにする必要がある（例：item_id、order_id）

    ・ActiveRecordがモデル間の関連付けを作成する時に参照される

- 主キー

    ・デフォルトではidという名前のintegerカラムがデーブルの主キーに使われる

    ・postgreSQL・MySQL→bigint

    ・SQLite→integer

- インスタンス機能を追加するカラム名

    ・created_at：レコード作成時に現在の日付時刻が自動的に設定される

    ・updated_at：レコード作成時や更新時に現在の保付時刻が自動的に設定される

    ・lock_version：モデルにoptimistic lockingを追加する

    ・type：モデルでSingle Table Inheritance を使う場合に指定

    ・関連付け名_type：ポリモーフィック関連付けの種類を保存

## rails newで生成されるコード

- bin/setup

    →リポジトリをgit cloneしたあと、１コマンドで開発環境を整えられる

- database.yml

    →データベースの接続設定を環境変数で指定できることが記載

- 開発環境のキャッシュの設定

    →キャッシュ設定をON/OFFする仕組みが用意

## Scaffoldコントローラー

- index, show
- create
- update

## 設計する時の流れ

1. 要点定義
2. 画面設計
3. リソースとDB設計
4. クラス設計
5. 実装

## 要件定義

- 実装する機能の目的を聞き出す
- その目的はコードを書かないで解決できないか
- 全体の仕様を最小の機能に分割し、依存関係を考える

## 画面設計

- 画像イメージをしっかり描く

→表示する項目を洗い出す

- 異常系を考えておく

→エラーメッセージの表示位置

## リソース設計

- RESTなルーティングを考える
- 必要なテーブルを考える

    ・テーブルはできるだけ正規化

    ・DBの制約は厳しく

## テーブル設計

- NOT NULL制約、ユニーク制約、外部キー制約などに気をつける

## 参考
https://www.notion.so/Rails-db8089b95254469eae8dddc0f87747b1#aa48488bcf1e4c1f81f86c0ec253bcc3
