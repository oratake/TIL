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

