# DB, SQL

## sql using

joinする場合、onで複数結合すると長くなって疲れる  
カラム名同じ場合はusingでよい

```sql
select * from tbl_hoge left join tbl_piyo using (user_id)
```

## サロゲートキー, ナチュラルキー

PKの考え方で出てくる  

- サロゲートキー(代理キー): 通しのauto_incrementなIDとかそれ
- ナチュラルキー(自然キー): 一意な名前とかハッシュとかをキーにするやつ

## ロック、トランザクションについて

MySQLのInnoDBのロック挙動調査 (いちりんめも)
- https://github.com/ichirin2501/doc/blob/master/innodb.md

Keyword: InnoDB, MySQL, トランザクション, ダーティリード, ファジーリード, ファントムリード, READ COMMITTED, REPEATABLE READ

## 参考URL

- AI Shift(CyberAgent子会社) SQL資料
https://speakerdeck.com/yutamiyake/sql-training-2021
  - データベース
  - SQL
    - キー
    - 集約関数
    - JOIN
  -トランザクション
    - ACID 特性
    - ファジー・ファントムリード
  - データベース設計
    - ER モデル
    - カーディナリティ
    - 正規形
  - ボイスコッド正規形
  - インデックス
    - B+ Tree
  - 実行計画
  - SQL II
