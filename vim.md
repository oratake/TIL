# Vim

## Tips

### 改行を削除

- 行数gJ
行数文、その下の行の改行をつぶす

### 改行,スペース,タブ削除

正規表現を使用

- 行末だけ
```
:%s/\s*$//
```

- 指定範囲全部
範囲指定してから
```
:%s/\s//
```

## Setting

### linux上でのnvimのクリップボード

neovimではクリップボードとの連携がないので、shell commandを使用する  
Linuxではxclipを使える

```
:set clipboard+=unnamedplus
```

`:help clipboard` 参照のこと

参考: https://qiita.com/gotchane/items/0e7e6e0d5c7fa9f55c1a
