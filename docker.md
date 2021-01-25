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

## alpineのビルドでapkでDNS解決できずコケる

参考: https://qiita.com/riita10069/items/9cb3a651be82052fc70d

```
Step 2/3 : RUN apk upgrade --update && apk --no-cache add   autoconf   make   g++   
gcc                                                                                 
 ---> Running in 2748003172b1                                                       
fetch https://dl-cdn.alpinelinux.org/alpine/v3.13/main/x86_64/APKINDEX.tar.gz       
ERROR: https://dl-cdn.alpinelinux.org/alpine/v3.13/main: DNS lookup error           
WARNING: Ignoring https://dl-cdn.alpinelinux.org/alpine/v3.13/main: No such file or 
directory                                                                           
fetch https://dl-cdn.alpinelinux.org/alpine/v3.13/community/x86_64/APKINDEX.tar.gz  
ERROR: https://dl-cdn.alpinelinux.org/alpine/v3.13/community: DNS lookup error      
WARNING: Ignoring https://dl-cdn.alpinelinux.org/alpine/v3.13/community: No such fil
e or directory                                                                      
OK: 13 MiB in 32 packages                                                           
fetch https://dl-cdn.alpinelinux.org/alpine/v3.13/main/x86_64/APKINDEX.tar.gz       
WARNING: Ignoring https://dl-cdn.alpinelinux.org/alpine/v3.13/main: DNS lookup error
fetch https://dl-cdn.alpinelinux.org/alpine/v3.13/community/x86_64/APKINDEX.tar.gz  
WARNING: Ignoring https://dl-cdn.alpinelinux.org/alpine/v3.13/community: DNS lookup 
error
...
```

/etc/resolv.conf
```
namespace 192.168.1.1 # これははじめからあった自宅のルータ
namespace 8.8.8.8 # GoogleのDNSをいれてみる
```
