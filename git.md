# Git

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

## configのautocrlf
windowsでgitを入れた場合、初期でcore.autocrlfがtrueにしようとする。  
trueの場合、checkoutでCRLF、commit時にLFに変換が走る。
inputの場合、checkoutで何もせず、commit時にLFに変換。
なので、PHPerならPSR-2に基づいてinputの設定でLFによせていいのでは。

## commitのAuthorを変更

configにnameとemailを設定しそびれて、別なAuthorでcommitされてしまった場合。

```
$ git commit --amend --author='oratake <smith.shimomura@gmail.com>'
```
