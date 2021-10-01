# Traefik-proxyのサンプル

## quick-start

開始以下の2つが存在しているが

+ ①開始(バックエンドとtraefik:プロキシサーバー全て起動)
+ ②それぞれ個別に開始(バックエンドとtraefik:プロキシサーバーそれぞれ起動)

```bash
# ①全開始(バックエンドとtraefik:プロキシサーバー全て起動)
# docker-compose -f 01_quick-start/docker-compose.yaml up

# ②それぞれ個別に開始(バックエンドとtraefik:プロキシサーバーそれぞれ起動)
# traefik起動
docker-compose -f 01_quick-start/docker-compose.yaml up -d reverse-proxy
# バックエンドのサービス追加1
docker-compose -f 01_quick-start/docker-compose.yaml up -d whoami-1
# バックエンドのサービス追加2
docker-compose -f 01_quick-start/docker-compose.yaml up -d whoami-2

# リクエスト
curl http://localhost:8090 -H Host:whoami-1.docker.localhost
curl http://localhost:8090 -H Host:whoami-2.docker.localhost

# 終了
docker-compose -f 01_quick-start/docker-compose.yaml down
```
```bash
# 起動
docker-compose -f quick-start/docker-compose.yaml up -d reverse-proxy
# 終了
docker-compose -f quick-start/docker-compose.yaml down
```

## 参考にすべきサイト

+ [docker-composeのポートを交通整理](https://qiita.com/koinori/items/39ab0c3048fdcfaf3f65)
