# docker-compose + bedrock 開発環境 

WordpressのボイラーテンプレートのBedrockの開発環境をDockerにて作成します

## インストール内容 
- [x] Mysql latest
- [x] nginx latest
- [x] composer latest
- [x] php 7.4.4

## 動作確認環境
- [x] Windows 10 pro 1909 (not use Hyper-V)
- [x] Docker 19.03.8
- [x] docker-compose 1.24.0
- [x] (mkcert)[https://github.com/FiloSottile/mkcert]

## 実行
1. `git clone git@git.dmm.com:tajima-kenji/docker-bedrock.git`
2. `cd docker-bedrock`
3. `mkcert -install`
4. `mkdir certs && cd certs`
5. `mkcert ${localdomain} localhost 127.0.0.1`
6. `cd ../`
7. `cp .env.template .env`
8. edit .env
9. `cd bedrock`
10. `cp .env.example .env`
11. edit .env
12. `cd ../`
13. `docker-compose up -d --build`
14. acsess `${NGINX_HOST}:${NGINX_HTTP_PORTS or NGINX_HTTPS_PORTS}`

## envの値について

- PRODUCT_NAME: dockerのプロダクト名です。
- VERSION_SQL: mySQLのimageのバージョンを指定します。
- MYSQL_PORTS: mySQLのポートを指定します。
- MYSQL_ROOT_PASSWORD: mySQLのルートパスワードを指定します。
- MYSQL_DATABASE: mySQLのデータベース名を指定します。
- MYSQL_USER: mySQLのユーザーを指定します。
- MYSQL_PASSWORD: mySQLのパスワードを指定します。
- LOCAL_USER: 自分のPCのコンソールのユーザーをPIDで指定します
- LOCAL_GROUP: 自分のPCのコンソールのユーザーのグループをPIDで指定します
- VERSION_NGINX: nginxのimageのバージョンを指定します。
- NGINX_HOST: nginxのホスト名を指定します。
- SSL_KEY: 5.で作成したkeyの.pem と -key.pem の前の名前を指定します
- NGINX_HTTP_PORTS: nginxにHTTPでアクセスした場合のポートです。
- NGINX_HTTPS_PORTS: nginxにHTTPSでアクセスした場合のポートです。
- UPLOAD_FILESIZE: アップロードできるファイルサイズです。
- MEMORY_LIMIT: PHP-FPMのメモリ上限です。
- MAX_EXECUTION_TIME: タイムアウトまでの待ち時間です。
- VERSION_PHP: phpのimageのバージョンを指定します。
- VERSION_COMPOSER: composerのimageのバージョンを指定します。
- BEDROCK_DIR: bedrockのディレクトリを指定します。
- WP_ROOT_DIR: webコンテナ内のbedrockが配置されるディレクトリを指定します。


## ユースケース

- ユーザーとグループのPIDってどうやって出せばいい？
`id` で自分のPIDが表示されます。
これを省くとpermissionでmysqlが立ち上がらない…

- Bedrockのcomposerをupdateしたい

1. `cd docker-bedrock`
2. `docker run --rm -v $PWD/bedrock:/app composer update`