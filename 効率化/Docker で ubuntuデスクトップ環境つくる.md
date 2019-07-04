# 参考
`https://hub.docker.com/r/uphy/ubuntu-desktop-jp/`
# docker image 取得
$ `docker pull uphy/ubuntu-desktop-jp`
# 確認
$ 'docker images'
# コンテナ起動
$ `docker run --rm -p 8080:8080 -it --name my-ubuntu-desktop uphy/ubuntu-desktop-jp:18.04`
# 確認
'http://localhost:8080'
