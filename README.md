# wordpress-docker-template

## 概要

docker-compose でローカル開発用の wordpress / mysql を 立ち上げるための基本設定です。

## 起動方法

```
$ cp .env.sample .env
$ docker-compose build
$ docker-compose up -d
```

## 動作確認

* http://localhost:5000/  # wordpress
* http://localhost:5001/  # phpMyAdmin

## 補足

### プラグイン

* プラグインの追加は、Dockerfile で行ってください。

```
...

# WP プラグイン (zip) ダウンロード
WORKDIR /tmp/wp-plugins
RUN wget https://downloads.wordpress.org/plugin/contact-form-7.5.1.1.zip  # プラグインを追加
RUN wget .....

...
```

* Dockerfile を更新したあとは、 `docker-compose build` および `./wordpress` ディレクトリの削除を行ってから `docker-compose up -d` してください。
* **<font color="Red">【注意】</font>** テーマ開発を `./wordpress/wp-content` 内で行っている場合、 `/wordpress` ディレクトリを単に削除するとまずいですね...。どなたか良い方法あれば教えてください。

```
$ docker-compose down  # コンテナを起動している場合は停止
$ docker-compose build
$ rm -rf ./wordpress  # /wordpress/wp-content/themes の退避が必要であれば適宜...mm
$ docker-compose up -d
```


### テーマ

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