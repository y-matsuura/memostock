### 公開鍵と秘密鍵をつくる
```
$ cd ~/.ssh

$ ssh-keygen -t rsa -b 4096 -C "matsuurayuji@gmail.com"
もしくは
$ ssh-keygen -t rsa

※デフォルトのファイル名は id_rsa となる。
変えたいときは別名を入力する。
例：id_rsa_git
```

### 公開鍵をgithubにアップする
#### 公開鍵をクリップボードにコピーするためにライブラリをインストールする
$ sudo apt install xsel

#### コピーする
$ cat id_rsa_git_local.pub | xsel --clipboard --input

#### githubにペーストする

#### 鍵の名前を別名にした場合はconfigに設定する
$ touch ~/.ssh/config

$ vim ~/.ssh/config
```
Host GitHub
  HostName github.com
  IdentityFile ~/.ssh/github/id_rsa_git_local
  TCPKeepAlive yes
  IdentitiesOnly yes
  User git
```

### 接続確認
$ ssh -T git@github.com
