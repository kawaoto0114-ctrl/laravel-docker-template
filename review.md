# Laravel Lesson レビュー①

## Todo一覧機能

### Todoモデルのallメソッドで実行しているSQLは何か
SELECT * FROM todos;

### Todoモデルのallメソッドの返り値は何か
Illuminate\Database\Eloquent\Collection

### 配列の代わりにCollectionクラスを使用するメリットは
複数のレコードをまとめて操作する（検索・絞り込み・並び替えなど）便利なメソッドを利用できるため。

### view関数の第1・第2引数の指定と何をしているか
第1因数は、todo/index.blade.phpを表示させている。
第2因数は、取得したTodoのデータ（$todos）を、Bladeにtodosという名前で渡している。

### index.blade.phpの$todos・$todoに代入されているものは何か
$todosには、データベースから取得したTodoの一覧（Collection）
$todoには、その中の1件のTodoモデルが代入されている

## Todo作成機能

### Requestクラスのallメソッドは何をしているか
リクエストで送られてきた入力データをすべて取得している。

### fillメソッドは何をしているか
引数（$inputs）に代入されている配列を$todoに代入している

### $fillableは何のために設定しているか
一括代入の項目に制限をかけるため

### saveメソッドで実行しているSQLは何か
INSERT INTO todos VALUES $todo

### redirect()->route()は何をしているか
Route()で指定したURLの画面へ移動する

## その他

### テーブル構成をマイグレーションファイルで管理するメリット
SQLを知らなくても、PHPコードでテーブル操作ができる
マイグレーションファイルを共有することで、同じテーブルを作成することができる

### マイグレーションファイルのup()、down()は何のコマンドを実行した時に呼び出されるのか
php artisan migrate
php artisan migrate:rollback

### Seederクラスの役割は何か
データベースにあるレコードを削除し、テストデータを挿入する

### route関数の引数・返り値・使用するメリット
引数はtodo.store、返り値はURL、メリットは同じURLからの送信でも違う処理ができること

### @extends・@section・@yieldの関係性とbladeを分割するメリット
@extendsで親Bladeを指定、
@sectionで子Bladeで内容を定義
@yieldで親Bladeで子Bladeの内容を表示

### @csrfは何のための記述か
トークンを生成し、アクセスする人の制限をかけている

### {{ }}とは何の省略系か
echo