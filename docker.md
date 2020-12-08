# Docker

おもに(Arch)Linux内でDocker使うやつ

## 情報

- [Awesome Docker](https://github.com/veggiemonk/awesome-docker)
dockerの情報スタック  
日本語まとめブログ  
https://wonderwall.hatenablog.com/entry/docker-awesome

- [Awesome Compose](https://github.com/docker/awesome-compose)
docker-composeのデザインパターン集  
GoとMySQLの例、みたいなのが乗ってる  

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
