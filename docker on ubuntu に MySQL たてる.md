## ▼使い捨て
https://budougumi0617.github.io/2018/05/20/create-instant-mysql-by-docker/





## ▼永続
### データボリュームコンテナの作成
$ docker pull busybox

### 永続化のためのデータ領域を作成
$ docker run -v /var/lib/mysql --name mysql_data busybox

### マウントして起動
$ docker run --volumes-from mysql_data --name mysql -v /home/vagrant/matsuura/docker:/home -e MYSQL_ROOT_PASSWORD=mysql -d -p 3306:3306 -p 80:80 -p 3000:3000 mysql:5.5




## 以下は現場での例
### コンテナにはいる
$ docker exec -it [コンテナID] bash

### コンテナのIPを確認
$ hostname -i
または
$ cat /etc/hosts

※以降はインテグレーション環境の構築手順を参照しつつ

### mysqlに接続
$ mysql -uroot -proot

### DBつくる
mysql> create database dns2_integration;

### USERつくる
mysql> create user 'cndns2'@'localhost' IDENTIFIED BY '{パスワード}';
mysql> create user 'cndns2'@'172.17.0.%' IDENTIFIED BY '{パスワード}';
[例]
create user 'cndns2'@'localhost' IDENTIFIED BY 'cndns2';
create user 'cndns2'@'172.17.0.%' IDENTIFIED BY 'cndns2';

### 権限与える
mysql> grant all on dns2_integration.* to 'cndns2'@'localhost';
mysql> grant all on dns2_integration.* to 'cndns2'@'172.17.0.%';

### USER確認
mysql> SELECT Host, User FROM mysql.user;

### 反映
mysql> flush privileges;

### 実行ユーザーでログインしなおす
mysql> quit;
$ mysql -ucndns2 -pcndns2 -Ddns2_integration

### 初期データ投入
$ mysql> source home/data/cloudn_dns_schema.sql;
$ mysql> source home/data/init.sql;
※以下のデータはsre-jenkinsで使われているもの。以下でも大丈夫。
dns_reset_data.sql
dns_init_data.sql
