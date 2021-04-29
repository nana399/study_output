# erbをslimに変更する
<br>

Railsにはもともとerbが搭載されている。
<br>
変更するには以下の手順を踏む必要がある。

`gemfile`

```markdown
gem 'slim-rails'
gem 'html2slim'
```

`ターミナル`

```markdown
% bundle
```

`ターミナル`

```markdown
% bundle exec erb2slim app/views/memos/ --delete
```
<br>

完成。

`app/views/memos/`

`memos/`
<br>
この部分を好みで変更する
