# 参考
https://qiita.com/rs_/items/6af6fe4d7858950e2062

# ubuntu LTS の image を取得する。※ここでは18.04
$ `docker pull ubuntu:18.04`
# 確認
$ `docker images`
# dockerコンテナ実行
$ `docker run -it -v /d/matsuura/self/docker/ubuntu/mydata:/var/www/html --name my-ubuntu ubuntu:18.04 -d`
```
参考
https://qiita.com/wMETAw/items/34ba5c980e2a38e548db

「-it」コンソールに結果を出力	
「-d」はデーモンの略でコンテナをバックグラウンドで起動させます。
「–name」でコンテナに名前をつけられる
```
# コンテナ実行結果確認
$ `docker ps`
# コンテナにはいる
$ `docker exec -it my-ubuntu bash`
