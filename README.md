# wordpress-docker

## 概要

docker-compose でローカル開発用の wordpress / mysql を 立ち上げるための基本設定です。

## 起動方法

`.env.sample` をコピーして `.env` を配備したうえで、docker-compose を起動してください。

```
$ cp .env.sample .env
$ docker-compose up -d
```

## 動作確認

* http://localhost:5000/  # wordpress
* http://localhost:5001/  # phpMyAdmin

