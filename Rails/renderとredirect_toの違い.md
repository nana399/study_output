# redirect_toとrenderの違い
 
```
・render　　　　　：　controller　→　view
・redirect_to　　　：　controller　→　URL　→　route　→　controller　→　view
 ```
<br>
renderは、アクションを実行せずにビューファイルを表示させるのに対し、
<br>
redirect_toは、１回指定したアクションを実行してそのアクションに対応したビューを表示させる。

 

# redirect_toとは
 
<br>
redirect_toは、
指定したURLに遷移させることができるメソッド
<br>
 redirect_toメソッドを使うと、決められたコントローラーのアクション以外のアクションなどを実行させ、選択したビューファイルを表示させることができる。

 
# redirect_toメソッドのリダイレクト先の指定
 

- パターン１：URLで指定する

`redirect_to "https://www.pokemon.co.jp/"`

- パターン２：アクションで指定

`redirect_to action: :new`
 

- パターン３：指定したコントローラのアクションで指定

`redirect_to  controller: :users, action: :show`

- パターン４：アクションの個別のリソースを指定

`redirect_to  controller: :users, action: :show, id: 1`
 

- パターン５：前のページを指定

`redirect_to :back`
 
<br>
その他にもステータスコードを指定してリダイレクトをさせることも可能。

 

# renderとは
 
<br>
renderは、Action内で、呼び出すViewを指定するメソッド
<br>
Action内でインスタンス変数として格納されたものは、viewから呼び出せる。

 

 

# 使い分け
 
```
データを追加、更新、削除を行う時 →「redirect_to」
データの取得を行う時 →「render」
```
 
<br>
controllerの処理が必要だー！といったものに対しては、redirect_toを使い、
<br>
失敗したらエラー表示させるだけでよいよーといったものに対しては、renderを使うといった感じ。

 

# 参考
 

[【Rails】renderとredirect_toの違いと使い分け - Qiita](https://qiita.com/morikuma709/items/e9146465df2d8a094d78)

[【Rails】redirect_toとrenderの使い分け - Qiita](https://qiita.com/jumpyoshim/items/ed10721c26963abdf121)

[renderとredirect_toの違いを整理 【Day 1/30 2nd】｜K.Tawara｜note](https://note.com/kentarotawara/n/nd8010d4d0649)

[【Rails】redirect_toの使い方を徹底解説！ | Pikawaka - ピカ1わかりやすいプログラミング用語サイト](https://pikawaka.com/rails/redirect_to)
