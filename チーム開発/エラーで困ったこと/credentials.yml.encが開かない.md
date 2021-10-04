# 状況
秘匿情報を登録しようとして以下のコマンドを実行した。

```rails
$ docker-compose run -e EDITOR=vim app rails credentials:edit
Creating team_app_app_run ... done
Adding config/master.key to store the encryption key: =======

Save this in a password manager your team can access.

If you lose the key, no one, including you, can access anything encrypted with it.

      create  config/master.key

Couldn't decrypt config/credentials.yml.enc. Perhaps you passed the wrong key?
```

### 内容としては、<br>
- `config/master.key`を作ったぞ〜<br>
- あっれ〜config/credentials.yml.を復号化出来んかったわ〜間違った鍵を渡した？といった内容である。

### 次に、
```rails
$ docker-compose run app rails credentials:show
Creating team_app_app_run ... done
/usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/message_encryptor.rb:203:in `rescue in _decrypt': ActiveSupport::MessageEncryptor::InvalidMessage (ActiveSupport::MessageEncryptor::InvalidMessage)
	from /usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/message_encryptor.rb:180:in `_decrypt'
	from /usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/message_encryptor.rb:154:in `decrypt_and_verify'
	from /usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/messages/rotator.rb:22:in `decrypt_and_verify'
	from /usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/encrypted_file.rb:92:in `decrypt'
	from /usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/encrypted_file.rb:54:in `read'
	from /usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/encrypted_configuration.rb:21:in `read'
	from /usr/local/bundle/gems/railties-6.1.4.1/lib/rails/commands/credentials/credentials_command.rb:50:in `show'
	from /usr/local/bundle/gems/thor-1.1.0/lib/thor/command.rb:27:in `run'
	from /usr/local/bundle/gems/thor-1.1.0/lib/thor/invocation.rb:127:in `invoke_command'
	from /usr/local/bundle/gems/thor-1.1.0/lib/thor.rb:392:in `dispatch'
	from /usr/local/bundle/gems/railties-6.1.4.1/lib/rails/command/base.rb:69:in `perform'
	from /usr/local/bundle/gems/railties-6.1.4.1/lib/rails/command.rb:48:in `invoke'
	from /usr/local/bundle/gems/railties-6.1.4.1/lib/rails/commands.rb:18:in `<main>'
	from /usr/local/bundle/gems/bootsnap-1.8.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `require'
	from /usr/local/bundle/gems/bootsnap-1.8.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `block in require_with_bootsnap_lfi'
	from /usr/local/bundle/gems/bootsnap-1.8.1/lib/bootsnap/load_path_cache/loaded_features_index.rb:92:in `register'
	from /usr/local/bundle/gems/bootsnap-1.8.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:22:in `require_with_bootsnap_lfi'
	from /usr/local/bundle/gems/bootsnap-1.8.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:31:in `require'
	from /app/bin/rails:5:in `<top (required)>'
	from /usr/local/bundle/gems/spring-2.1.1/lib/spring/client/rails.rb:28:in `load'
	from /usr/local/bundle/gems/spring-2.1.1/lib/spring/client/rails.rb:28:in `call'
	from /usr/local/bundle/gems/spring-2.1.1/lib/spring/client/command.rb:7:in `call'
	from /usr/local/bundle/gems/spring-2.1.1/lib/spring/client.rb:30:in `run'
	from /usr/local/bundle/gems/spring-2.1.1/bin/spring:49:in `<top (required)>'
	from /usr/local/bundle/gems/spring-2.1.1/lib/spring/binstub.rb:11:in `load'
	from /usr/local/bundle/gems/spring-2.1.1/lib/spring/binstub.rb:11:in `<top (required)>'
	from <internal:/usr/local/lib/ruby/3.0.0/rubygems/core_ext/kernel_require.rb>:85:in `require'
	from <internal:/usr/local/lib/ruby/3.0.0/rubygems/core_ext/kernel_require.rb>:85:in `require'
	from /app/bin/spring:10:in `block in <top (required)>'
	from <internal:kernel>:90:in `tap'
	from /app/bin/spring:7:in `<top (required)>'
	from bin/rails:2:in `load'
	from bin/rails:2:in `<main>'
/usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/message_encryptor.rb:198:in `final': 

	from /usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/message_encryptor.rb:198:in `_decrypt'
	from /usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/message_encryptor.rb:154:in `decrypt_and_verify'
	from /usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/messages/rotator.rb:22:in `decrypt_and_verify'
	from /usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/encrypted_file.rb:92:in `decrypt'
	from /usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/encrypted_file.rb:54:in `read'
	from /usr/local/bundle/gems/activesupport-6.1.4.1/lib/active_support/encrypted_configuration.rb:21:in `read'
	from /usr/local/bundle/gems/railties-6.1.4.1/lib/rails/commands/credentials/credentials_command.rb:50:in `show'
	from /usr/local/bundle/gems/thor-1.1.0/lib/thor/command.rb:27:in `run'
	from /usr/local/bundle/gems/thor-1.1.0/lib/thor/invocation.rb:127:in `invoke_command'
	from /usr/local/bundle/gems/thor-1.1.0/lib/thor.rb:392:in `dispatch'
	from /usr/local/bundle/gems/railties-6.1.4.1/lib/rails/command/base.rb:69:in `perform'
	from /usr/local/bundle/gems/railties-6.1.4.1/lib/rails/command.rb:48:in `invoke'
	from /usr/local/bundle/gems/railties-6.1.4.1/lib/rails/commands.rb:18:in `<main>'
	from /usr/local/bundle/gems/bootsnap-1.8.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `require'
	from /usr/local/bundle/gems/bootsnap-1.8.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:23:in `block in require_with_bootsnap_lfi'
	from /usr/local/bundle/gems/bootsnap-1.8.1/lib/bootsnap/load_path_cache/loaded_features_index.rb:92:in `register'
	from /usr/local/bundle/gems/bootsnap-1.8.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:22:in `require_with_bootsnap_lfi'
	from /usr/local/bundle/gems/bootsnap-1.8.1/lib/bootsnap/load_path_cache/core_ext/kernel_require.rb:31:in `require'
	from /app/bin/rails:5:in `<top (required)>'
	from /usr/local/bundle/gems/spring-2.1.1/lib/spring/client/rails.rb:28:in `load'
	from /usr/local/bundle/gems/spring-2.1.1/lib/spring/client/rails.rb:28:in `call'
	from /usr/local/bundle/gems/spring-2.1.1/lib/spring/client/command.rb:7:in `call'
	from /usr/local/bundle/gems/spring-2.1.1/lib/spring/client.rb:30:in `run'
	from /usr/local/bundle/gems/spring-2.1.1/bin/spring:49:in `<top (required)>'
	from /usr/local/bundle/gems/spring-2.1.1/lib/spring/binstub.rb:11:in `load'
	from /usr/local/bundle/gems/spring-2.1.1/lib/spring/binstub.rb:11:in `<top (required)>'
	from <internal:/usr/local/lib/ruby/3.0.0/rubygems/core_ext/kernel_require.rb>:85:in `require'
	from <internal:/usr/local/lib/ruby/3.0.0/rubygems/core_ext/kernel_require.rb>:85:in `require'
	from /app/bin/spring:10:in `block in <top (required)>'
	from <internal:kernel>:90:in `tap'
	from /app/bin/spring:7:in `<top (required)>'
	from bin/rails:2:in `load'
	from bin/rails:2:in `<main>'
ERROR: 1
```

このコマンドから、
`ActiveSupport::MessageEncryptor::InvalidMessage (ActiveSupport::MessageEncryptor::InvalidMessage)`といったエラーと、
`OpenSSL::Cipher::CipherError`が発生していることがみてとれる
  

## なぜエラーが起きたのか

### ❐前提条件
- rails new すると、`config/credentials.yml.enc` と `config/master.key` は自動的に作られる。
- `config/master.key` は.gitignoreによって、git管理されないようになっている。
- cloneしても `config/master.key` の情報は知ることができない。

### ❐rails credentials:editコマンドがやっていること
- 基本的には秘匿情報の登録を行うコマンド。
- しかし、鍵が存在しない場合は勝手に鍵を生成して、<br>
`config/master.key`に鍵情報を新規作成し保存する。<br>

### ❐ActiveSupport::MessageEncryptor::InvalidMessage
- 新しく生成した鍵が既存の`credentials.yml.erc`に対応していないということを知らせるエラー。

## 解決方法1. 
/config/master.keyが共有できない環境ではmaster keyを環境変数：RAILS_MASTER_KEYで指定する

```
$ export RAILS_MASTER_KEY="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```
## 解決方法2.
既存のcredential.yml.ercに接続したい場合は、<br>
以前共有されたマスターキーをもとに、config/master.keyファイルを作成し、その後<br>
```
$ docker-compose run -e EDITOR=vim app rails credentials:edit
```
を打てば`credentials.yml.enc`の復号化できる

# 参考情報
- [EDITOR=vi rails credentials:editするもCouldn't decrypt config/credentials.yml.enc. Perhaps you passed the wrong key?と言われる](https://qiita.com/zenfumi/items/4a7cbab59f0f7ede0d6e)
- [Rails 5.2 で ActiveSupport::MessageEncryptor::InvalidMessage](https://qiita.com/scivola/items/cc06ddbfd94d3118f693)
- [EDITOR=vim rails credentials:editを実行すると「ActiveSupport::MessageEncryptor::InvalidMessage」と言われる](https://qiita.com/kenz-dev/items/67ac14d1c89f7c5641c1)
- [Rails5.2から追加された credentials.yml.enc のキホン](https://qiita.com/NaokiIshimura/items/2a179f2ab910992c4d39)
