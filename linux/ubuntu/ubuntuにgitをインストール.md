### バージョン確認
$ git --version

### 古いgitが存在する場合など削除する
※もちろん、無理に削除しなくてよい
#### gitパッケージのみ削除
$ sudo apt remove git

#### gitパッケージと依存パッケージを削除
$ sudo apt remove --auto-remove git

### 最新のgitをダウンロード
$ sudo add-apt-repository ppa:git-core/ppa

$ sudo apt update

$ sudo apt install git

[参考]
https://git-scm.com/download/linux

### バージョン確認
$ git --version
※最新が入っていれば成功
