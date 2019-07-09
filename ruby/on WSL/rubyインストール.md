# 参考
https://qiita.com/go_d_eye_0505/items/44d12ef0d52b2dc9d560
https://qiita.com/yatumine/items/2d421d36dbcbfb970e4e

# rbenvインストール
## git clone
$ `git clone https://github.com/sstephenson/rbenv.git ~/.rbenv`
## rbenvインストール
$ `sudo apt install rbenv`
## パスを通す
```
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
$ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
```
## rbenvのバージョン確認
$ `rbenv --version`

# ruby-buildインストール
## git clone
$ `git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build`
## ruby-buildディレクトリに移動し、install.shを実行
```
$ cd ruby-build/
$ sudo ./install.sh
```

# パッケージインストール
## gcc
$ `sudo apt install gcc`
## make
$ 'sudo apt install make'
## libssl-dev
$ `sudo apt install libssl-dev`

# インストールできるrubyを確認
$ 'rbenv install --list'
# rubyインストール
$ `rbenv install 2.6.2`
# globalに反映
$ `rbenv global 2.6.2`
# 
