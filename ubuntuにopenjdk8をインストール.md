[参考]
https://qiita.com/terappy/items/537c069923144a9d9755

### ubuntuのバージョンを確認
$ cat /etc/os-release

### Openjdkのバージョンを検索
$ sudo apt search openjdk-\(\.\)\+-jdk$

### Java8をインストール
$ sudo apt install openjdk-8-jdk

### バージョン確認
$ java -version
$ javac -version
