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