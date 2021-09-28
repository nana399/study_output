# pry-railsの使い方
  1. 調べたい箇所に `binding.pry` を記述する
  2. consoleをたちあげる
  3. pry(#<UsersController>)> `params`　と入力
  →中身の情報をみることができる
  4. ] pry(#<UsersController>)> `login(params[:user][:email], params[:user][:password])er][:password])`をすることで、ログイン情報の中身をみることができる
  5. pry(#<UsersController>)> `@user = User.new(user_params)`と入力するとuser情報をみることができる
  ６. pry(#<UsersController>)> @user.saver>)> `@user.save`でuser情報を保存できる
