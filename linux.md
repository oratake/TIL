# Linux

## GNOME Autostart
自動起動 Gnomeの場合。  
Source: https://mseeeen.msen.jp/centos74-gnome-startup-script/

全ユーザ: `/etc/xdg/autostart/`  
ユーザ設定: `~/.config/autostart/`  
この中の`*.desktop` が実行されるため、desktopファイルをコピー。

**スクリプト実行をしたい場合**
スクリプトを叩くための `.desktop` を用意

```
[Desktop Entry]
Name=Startup Settings
Type=Application
Exec=/startup/path/is/here.sh
OnlyShowIn=GNOME;
NoDisplay=true
```

OnlyShowInでWMを指定する。

スクリプト  
Shebangから書き始める

```
#!/usr/bin/bash

setxkbmap -option ctrl:nocaps
xset r rate 190 26
```

## パッケージマネージャ (UbuntuとArchのちがい)

Archはだいたい `pacman -S foobar` でいける。その他もリポジトリ設定などせずとも、だいたいAUR `yay -S foobar` とかで行ける
Ubuntuの場合、 `apt install foobar` か、ない場合は汎用の `snap install foobar` をつかう。

## よく使うディレクトリ

### Ubuntu

- font
  - /usr/share/fonts/
  - fonts以下に種類、それ以下にフォントファミリごとディレクトリ切ってるのをよくみる
