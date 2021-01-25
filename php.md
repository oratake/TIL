# PHP

## ない系判定

$_POST['hoge']

|null|そもそもnameで指定されてない|
|'' (空文字)|内容が入力されていない|

## csv

パース `fgetcsv()`  
fopenとかで開いたファイルポインタを渡して、そのレコードをパース

書き込み `fputcsv($filepointer, $data_array, ",")`  
第3引数はデリミタ。第4引数がエンクロージャ。ただしエンクロージャを指定しなくても必要な場合は自動でやってくれる

## PDO

https://www.php.net/manual/ja/pdo.prepare.php

PDOでクエリ流す場合、3種類ぐらいやり方がある

- PDO::exec()
returnがinsertされた行数。select文でとっても値取り出せない。
- PDO::query()
returnがPDOStatementで、select文など結果を返す
- PDOStatement::execute()
プリペアドステートメント。セキュリティ上、PDOでDB操作やるならこれでよさそう
