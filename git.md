# Git

## CheatSheet

### .gitignore (gibo自動生成)

giboはaptにはなさそう。archはAURにありそう。linuxbrewとmacは以下
```
$ brew install gibo
```

リスト
```
$ gibo list | grep -i jav #パイプで渡して検索できる
```

dumpのサンプル
```
$ gibo dump visualstudio jetbrains node >> .gitignore
```

## Remote URLをhttpsにしたときの認証
トークンを発行して、passwordの入力にいれて使う。  
remote urlがsshの場合は、ssh公開鍵を使う従来の方法。httpsを使ったほうが、若干速度が出るかも？

https://help.github.com/ja/github/using-git/which-remote-url-should-i-use#cloning-with-https-urls-recommended

## mergeの方向
思ってたんと違った。  
topic -> master ブランチに変更をmergeする場合
```
$ git checkout master
$ git merge topic
```

## rebaseでtopicをmasterに追いつかせる

編集中のtopic(feature)ブランチを、本流(master)にのせかえて(rebase)最新の状態に追いつかせる  

`topic` を `master` に `rebase`

```
$ git checkout topic
$ git rebase master
## もしくは...
$ git rebase master topic
```

## rebase --ontoで詳細に指定

`--onto` のあと3つ続けて指定

```
$ git rebase --onto 根っこに指定したいコミット いまの根っこ 動かしたいブランチ
```

## configのautocrlf
windowsでgitを入れた場合、初期でcore.autocrlfがtrueにしようとする。  
trueの場合、checkoutでCRLF、commit時にLFに変換が走る。  
inputの場合、checkoutで何もせず、commit時にLFに変換。  
なので、PHPerならPSR-2に基づいてinputの設定でLFによせていいのでは。

## commitのAuthorを変更

configにnameとemailを設定しそびれて、別なAuthorでcommitされてしまった場合。

```
$ git commit --amend --author='username_is_here <here.is.your@mail.address>'
```

もしくは、configに設定を記述したあと以下でも

```
$ git commit --amend --reset-author
```

過去全てのauthorを変更して良ければ

```
$ git filter-branch -f --env-filter \
  "GIT_AUTHOR_NAME='new'; \
   GIT_AUTHOR_EMAIL='new@example.com'; \
   GIT_COMMITTER_NAME='new'; \
   GIT_COMMITTER_EMAIL='new@example.com';" \
   HEAD
```

参照: https://qiita.com/y10exxx/items/dcea0e39788d649ca8ba

## switchとrestore (バイバイcheckout)
checkoutの責務がでかい。ので git -v 2.23 より switch/restore が採用。

### switch

```
$ git checkout -b hogepiyo
$ git switch -c hogepiyo
```

### restore

```
$ git checkout .
$ git restore .
```

## ブランチ名がない (HEAD)

rebase で squash したら、元のブランチが残って、別なブランチが生えてしまった  
そしてなぜかブランチ名がなくなった。  
派生元のコミットから生えているが、HEADとしか書かれておらず、ブランチ名ではなくコミットハッシュが表示されていた

対処
```
# とりあえずHEAD上でブランチ切る
$ git checkout -b <BRANCH>
```

## resetで取り消す

gitにおける状態の理解から

|用語|状態|
|---|---|
|HEAD|最新のコミット|
|index|最新のステージング|
|working tree|現状のファイル|

を踏まえて操作対象は以下の通り

|git reset hoge|HEAD|index|working tree|
|---|---|---|---|
|--soft|○|||		
|(no option)|○|○||
|--hard|○|○|○|

## 間違って本流ブランチでコミットを積んじゃったので別ブランチにする

`master` に積みまくった。ほんとは `feature-hoge_piyo` にするつもりだった。  

```
$ git switch -c <本来切りたかったコミット名>
$ git switch <本流ブランチ>
$ git reset --hard <分岐元コミットハッシュ>
# 最後にoriginと合わせる必要があれば合わせる
$ git push -f origin
```

## cherry-pick

他のブランチから一部持ってきたい、などの場合

```
$ git cherry-pick -e <commit_hash>
```

-e でエディタが開き、コミットコメントの編集をしつつ持ってこれる。
