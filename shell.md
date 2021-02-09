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

## 配列とそのforeach

複数バッチに開始日と終了日を指定して実行、みたいな例

```
#!/bin/bash
# usage: ./hogepiyo.sh <start-date> <end-date>

# 開始日、終了日
start=$1
end=$2

# 実行するスクリプト
scripts=(
    script1.sh
    script2.sh
    # その他いっぱい...
)

for script in ${scripts[@]}
do
    echo ${script}
    echo "--------------------" 
    ./${script} ${start} ${end}
done
```

## less

大体ここ参照: https://qiita.com/delphinus/items/b04752bb5b64e6cc4ea9

### 色付きで表示

`docker-compose logs` なんかをパイプでlessに渡して見たいケース。普通にやると ANSI カラーエスケープシーケンスでごちゃごちゃになるが、  
```
$ docker-compose logs | less -R +F
```
これでOK。+F は `tail -f` 同様、logが増えても最新を追うやつ
