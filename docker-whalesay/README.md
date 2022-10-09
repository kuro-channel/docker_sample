# docker-whalesay
### FROM
- `FROM`：元になるイメージを指定
- `fortunes`：格言を表示するコマンド
- `docker build -t docker-whale .` : Dockerfileからイメージをビルドする
  - .（ビルドコンテキスト）上のDockerfileを実行する
  - .（ビルドコンテキスト）には不要なファイルは載せないようにしよう
- `docker run docker-whalesay`

### 参考文献
【Docker】[failed to load cache key: invalid empty config file resolved] を解決した方法 (備忘録)
https://qiita.com/Ryo-Nakano/items/f1a3af717ac62292387c

dockerでWhalesayイメージがpull(run)できない時の対処法
https://qiita.com/nasuB7373/items/92166d7958044ab8d450