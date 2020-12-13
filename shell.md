# Shell

## Shebang `#!/bin/bash`

Keyword: Shebang, シバン, シェバン, /bin/sh

大体以下で解決した  
https://qiita.com/mohira/items/566ca75d704072bcb26f

Shebangはインタプリタの指定になっているので、 `#!` 以降が引数として渡される

./sample04.rb

```
#!/usr/bin/env ruby
// ruby script
...
```

```
$ /usr/bin/env ruby ./sample04.rb
↑等価↓
$ ./sample04.rb
```

## いまのShellを表示

ユーザの起動SHELLを表示 (環境変数$SHELLに入っているのでecho)

```
$ echo $SHELL
```

今ちょうど使っているshellの表示

```
$ echo $0
```

## zshrcなどの読み込み順

zshrnv > zprofile > zshrc > zlogin
各々、global ( /etc/* ), local ( ~/.* ) の順で読まれる

https://qiita.com/muran001/items/7b104d33f5ea3f75353f

## ファイル名フックしてその中身全部からgrep

例: phpファイルから
`$ find ./src/ -type f -name "*php" | xargs grep -n "hogepiyo_114514`

## エイリアスを一時的に無効化

.zshrc等でつけていたエイリアスをその場だけ無効にして実行したい場合は、コマンドをエスケープ

```
$ \docker-compose ps -a
```

そのセッション中無効にしたいなら

```
$ unalias d-c # これでもともとsudo docker-composeされていたのが、d-cのエイリアスが剥がれる
```
