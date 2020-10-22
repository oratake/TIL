# SQL

## using

joinする場合、onで複数結合すると長くなって疲れる
カラム名同じ場合はusingでよい

```sql
select * from tbl_hoge left join tbl_piyo using (user_id)
```
