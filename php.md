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

## \Throwable

javaとか同様、\Throwable は PHP でもErrorとかException全部のスーパークラスみたいな  
(クラスというか実際はインターフェース)

> Throwable は、throw 文でスロー可能なあらゆるオブジェクトが実装する基底インターフェイスです。 Error や Exception も、これを実装しています。  
https://www.php.net/manual/ja/class.throwable.php

catch (\Throwable $e) で全部とれる

Throwable みたいなノリで、「〜できる性質を付加」みたいな意味合いで Hogeable みたいなクラス作る場合あり (Generatableとか)  
phpならinterfaceとかtraitでつくる人多いそうな
