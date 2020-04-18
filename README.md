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

## 実行(WIP)
1. `git clone git@git.dmm.com:tajima-kenji/docker-bedrock.git`
2. `cd docker-bedrock`
3. `cp .env.template .env`
4. edit .env
5. move docker Execution environment
6. `docker-compose up -d --build`