# wordpress-docker

## 概要

docker-compose でローカル開発用の wordpress / mysql を 立ち上げるための基本設定です。

## 起動方法

1. .env.sample をコピーして、.env を配備
2. `$ docker-compose up -d`

http://localhost:5000/  # wordpress
http://localhost:5001/  # phpMyAdmin