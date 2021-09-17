# Git stashとは
「変更を一時退避する処理」のこと。<br>
まだコミットはしたくない修正を、一時退避するために用いる。

### 使い方
```
git stash [実行コマンド]
```

## 「git stash save」
作業中のファイルを保存する
```
$ git stash save "任意のメッセージ"　
（例）　$ git stash save "一時退避"
```

## 「git stash list」で退避できているかの確認
保存したリストを確認する<br>
実行時には以下のように情報が出力される。
```
「stash@{番号}」: On 「ブランチ名」: 「メッセージ」
（例） stash@{0}: On master: 一時退避
```
## 「git stash apply」で復旧作業

```
$ git stash apply 復旧したいstash名
```
名前を省略すると、一番最新のstashが復旧する。
stash名は`git stash list`で取得できる

復旧させたいsatsh名が「stash@{0}」だったら、
```
git stash apply stash@{0}
```
とコマンドを打てばよい。

## 「git stash drop」で退避データを削除!
復旧が無事完了したら、退避しているデータは削除させる。

```
git stash drop stash@{0}
```
名前部分を省略すると、一番最新のstashを削除する。

# 番外編
## 変更差分を調べるなら「git diff」
現在stashしている内容を、確認したい時は`diffコマンド`を使用する

```
git diff stash@{0}
```
`「--name-only」オプション`をつけることで、変更のあるファイル名のみ探すことも可能。
```
git diff --name-only stash@{0}
```

ファイル名を指定することで、指定ファイルの差分のみ表示することが可能

```
git diff stash@{0} ファイル名
```

# applyとdropを同時に!「git stash pop」
`stash popコマンド`を使用することで`apply`と`drop`コマンドを同時に行うことができる。

```
git stash pop stash@{0}
```
これをすることで、復旧と削除が同時に行える。

# 参考サイト
- [変更を一時的に退避しよう!git stashを使いこなす5つのステップ](https://www.sejuku.net/blog/71428)
