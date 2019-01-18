# wordpress-docker-template

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

## 補足

* wordpress のテーマ開発を別リポジトリ（別のローカルディレクトリ）で行う場合、 `docker-compose.yml` でそのディレクトリをボリュームマウントしてください。

``` docker-copmose.yml
  ...

  wordpress:
    ...
    volumes:
      - ./wordpress:/var/www/html
      - /path/to/myTheme:/var/www/html/wp-content/themes/myTheme # 別リポジトリでテーマ開発をする場合
    ports: 
      ...
```