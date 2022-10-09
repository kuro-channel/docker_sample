# docker-nginx
- nginxのdockerImageを使用してWebサーバーを立ててみよう

## nginx：デフォルト表示
- docker Hubのnginxイメージを確認、Exposing external portを使用する
https://hub.docker.com/_/nginx

```
Exposing external port
$ docker run --name some-nginx -d -p 8080:80 some-content-nginx
Then you can hit http://localhost:8080 or http://host-ip:8080 in your browser.
```

## nginx：静的なhtmlを表示させてみる
- docker Hubのnginxイメージを確認、Hosting some simple static content　を確認する
```
Hosting some simple static content
$ docker run --name some-nginx -v /some/content:/usr/share/nginx/html:ro -d nginx
Alternatively, a simple Dockerfile can be used to generate a new image that includes the necessary content (which is a much cleaner solution than the bind mount above):

FROM nginx
COPY static-html-directory /usr/share/nginx/html
Place this file in the same directory as your directory of content ("static-html-directory"), run docker build -t some-content-nginx ., then start your container:

$ docker run --name some-nginx -d some-content-nginx
```


### 各種コマンド
- nginxのコンテナを立ち上げるコマンド
  - `$docker run --name <コンテナ名> -d \-p <ホスト側のポート番号>:<コンテナ側のポート番号> \ <イメージ名>`
  - `docker run --name test-nginx -d -p 8080:80 nginx`
  - `-d` をつけない：フォアグラウンドで実行されている

### 超重要：ホストマシン上のディレクトリをdocker上にマウントする
- ホストマシンと同期させて静的なファイルを表示させる
  - `$docker run --name <コンテナ名> -d \ -v <ホスト側のディレクトリ>:<コンテナ側のマウントポイント>:オプション \ -p <ホスト側のポート番号>:<コンテナ側のポート番号> \ <イメージ名>`
  - `docker run --name some-nginx -v /some/content:/usr/share/nginx/html:ro -d nginx`
  - roオプション：マウント先で読み取り専用にする
  - `docker run --name first-nginx -v C:/Users/XXXX/Documents/docker_sample/docker-nginx/html/:/usr/share/nginx/html:ro -d -p 8080:80 nginx`

- ホスト側にあるディレクトリをコンテナにマウントする