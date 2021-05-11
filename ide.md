# IDE

## PHPStorm ideaVim で相対行表示

プラグイン Relative Line Numbers を使用

https://www.karakaram.com/ideavim-relative-line-number

## .editconfig

さまざまなIDEやエディタで統一のコーディングスタイルを設定したいときに

- .gitignoreの参考
```
root = true #現在のディレクトリ以下も同様の設定を適用

[*]
end_of_line = lf
charset = utf-8
insert_final_newline = true
trim_trailing_whitespace = true

[*.{json,scss,ts,tsx,yml}]
indent_style = space
indent_size = 2

[Makefile]
indent_style = tab
```

