# Docker

おもにLinux内でDocker使うやつ

## やらかしたときの初期化

`/var/lib/docker/`の削除
キーも何もかもぶっ壊すので注意

```
pacman -R docker
reboot
rm -rf /var/lib/docker/
rm -rf /etc/docker/
pacman -Sy docker
systemctl enable docker
systemctl start docker
```

参考: https://qiita.com/tukiyo3/items/0ad77d857342e747731f
