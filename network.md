# Network
## 同じセグメントの端末のIPを一覧表示
`netdiscover -r 192.168.0.1/24`
表示例
```
 Currently scanning: Finished!   |   Screen View: Unique Hosts

 18 Captured ARP Req/Rep packets, from 10 hosts.   Total size: 1080
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname
 -----------------------------------------------------------------------------
 192.168.0.1     ここにMACアドレス       2     120  HOGEPIYO Co., Ltd.
 192.168.0.10    10:6f:3f:なんとか      1      60  BUFFALO.INC #このへんNAS
 192.168.0.11    50:ed:3c:なんとか      1      60  Apple, Inc.
 192.168.0.3     f4:3b:d8:なんとか      1      60  Intel Corporate #適当なPC
 192.168.0.201   34:76:c5:なんとか      1      60  I-O DATA DEVICE,INC. #無線LAN AP
 グローバルっぽいIP   ここにMACアドレス      1      60  HOGEPIYO Co., Ltd. #1行目のONUと同じやつ?
```
