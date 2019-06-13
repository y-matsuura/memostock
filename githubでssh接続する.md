#### 参考
https://qiita.com/shizuma/items/2b2f873a0034839e47ce

#### 秘密鍵を入れるディレクトリに移動する
$ cd ~/.ssh

#### 鍵を生成する。ファイル名は任意。パスフレーズはなくても大丈夫。
$ ssh-keygen -t rsa -C "matsuurayuji@gmail.com"

#### 公開鍵をgithubに登録する
##### 公開鍵を中身をコピーする（linuxの場合）
$ cat id_rsa_git.pub | xsel --clipboard --input

##### xselが存在しない場合
$ sudo apt install xsel

#### 接続を確認する
$ ssh -T git@github.com
