# Traefik-proxyのサンプル

## quick-start

### Traefikとバックエンド2つのシンプルな構成

```bash
# 起動
docker-compose -f 01_quick-start/traefik-and-whoami.yaml up

# ※個別に起動する場合
# traefik起動
# docker-compose -f 01_quick-start/traefik-and-whoami.yaml up -d reverse-proxy
# バックエンドのサービス追加1
# docker-compose -f 01_quick-start/traefik-and-whoami.yaml up -d whoami-1
# バックエンドのサービス追加2
# docker-compose -f 01_quick-start/traefik-and-whoami.yaml up -d whoami-2

# リクエスト
curl http://localhost:8090 -H Host:whoami-1.localhost
curl http://localhost:8090 -H Host:whoami-2.localhost

# 終了
docker-compose -f 01_quick-start/traefik-and-whoami.yaml down
```

**ブラウザで開く場合**

+ `http://whoami-1.localhost:8090/`
+ `http://whoami-2.localhost:8090/`

### Traefikとバックエンド2つのシンプルな構成（別バージョン）

```bash
# 起動
docker-compose -f 01_quick-start/traefik-and-otherwhoami.yaml up

# ※個別に起動する場合
# traefik起動
# docker-compose -f 01_quick-start/traefik-and-otherwhoami.yaml up -d reverse-proxy
# バックエンドのサービス追加1
# docker-compose -f 01_quick-start/traefik-and-otherwhoami.yaml up -d whoami-c
# バックエンドのサービス追加2
# docker-compose -f 01_quick-start/traefik-and-otherwhoami.yaml up -d whoami-j

# リクエスト
curl http://localhost:8090 -H Host:whoami-c.localhost
curl http://localhost:8090 -H Host:whoami-j.localhost

# 終了
docker-compose -f 01_quick-start/traefik-and-otherwhoami.yaml down
```

**ブラウザで開く場合**

+ `http://whoami-c.localhost:8090/`
+ `http://whoami-j.localhost:8090/`

## keycloak

```bash
# プロキシサーバー 起動
docker-compose -f 02_keycloak/traefik-proxy/docker-compose.yaml up -d

# keycloak 起動
docker-compose -f 02_keycloak/keycloak-app/docker-compose.yaml up -d

# keycloak 終了
docker-compose -f 02_keycloak/keycloak-app/docker-compose.yaml down

# プロキシサーバー 終了
docker-compose -f 02_keycloak/traefik-proxy/docker-compose.yaml down
```

**ブラウザで開く場合**

+ `http://keycloak.localhost:8090/`

## 参考にしたサイト

+ [Traefik公式：QuickStart](https://doc.traefik.io/traefik/getting-started/quick-start/)
+ [シンプルなtraefikの例](https://johnny.am/blog/simple-traefik-setup-with-docker-x5)
+ [docker-composeのポートを交通整理](https://qiita.com/koinori/items/39ab0c3048fdcfaf3f65)
+ [traefikの例](https://www.casleyconsulting.co.jp/blog/engineer/240/)
+ [StackOverflow公式:traefikのポートフォワーディング](https://stackoverflow.com/questions/63173014/port-forwarding-with-traefik-and-docker-compose)
