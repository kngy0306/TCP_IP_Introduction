# TCP_IP_Introduction

## Docker構築参考

https://github.com/koboriakira/tcp_ip_guide

## 初期化

```sh
docker build -t tcp_ip_guide_image .

docker run -it --privileged --name tcp_ip_guide tcp_ip_guide_image
```

## 2回目以降の起動

```sh
# コンテナ起動
docker start tcp_ip_guide

# ログイン
docker exec -it --privileged tcp_ip_guide bash

# コンテナ停止
docker stop tcp_ip_guide
```

## #1 はじめに

環境：Ubuntu 18.04  

## #2 TCP/IPとは

### 通信する

ping ... TCP/IPでネットワークの疎通を確認するコマンド。ICMPというプロトコルが使用されている。ICMPの`echo request`を送信し、`echo reply`を受け取っている。IPによって運ばれる。

```sh
ping -c 3 8.8.8.8

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=37 time=92.5 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=37 time=12.4 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=37 time=14.8 ms
```

8.8.8.8はGoogleが運用する公開DNSサーバ。

### パケットキャプチャする

```sh
tcpdump -i any icmp

# 別タブでpingを実行する

tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 262144 bytes
IP 172.17.0.2 > 8.8.8.8: ICMP echo request, id 54, seq 1, length 64
IP 8.8.8.8 > 172.17.0.2: ICMP echo reply, id 54, seq 1, length 64
IP 172.17.0.2 > 8.8.8.8: ICMP echo request, id 54, seq 2, length 64
IP 8.8.8.8 > 172.17.0.2: ICMP echo reply, id 54, seq 2, length 64
IP 172.17.0.2 > 8.8.8.8: ICMP echo request, id 54, seq 3, length 64
IP 8.8.8.8 > 172.17.0.2: ICMP echo reply, id 54, seq 3, length 64
```

オプションの意味参考 → https://www.ibm.com/docs/ja/aix/7.2?topic=t-tcpdump-command#tcpdump__row-d3e79923

