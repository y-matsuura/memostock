[参考]
https://qiita.com/tkyonezu/items/0f6da57eb2d823d2611d

### パッケージインデックスの更新
$ sudo apt update

### 必要なパッケージをインストール
$ sudo apt install -y \
apt-transport-https \
ca-certificates \
curl \
software-properties-common

### docker公式のGPG公開鍵をインストール
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

### 公開鍵のフィンガープリントを確認
$ sudo apt-key fingerprint 0EBFCD88

### aptリポジトリの設定
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

### docker-ceのインストール
$ sudo apt update
$ sudo apt-get install -y docker-ce

### バージョン確認
$ docker version

## docker コマンドに sudo を付けなくてすむように
### dockerグループがなければ作る
$ sudo groupadd docker

### 現行ユーザをdockerグループに所属させる
$ sudo gpasswd -a $USER docker

### dockerデーモンを再起動する (CentOS7の場合)
$ sudo systemctl restart docker

### 再起動
$ sudo reboot
