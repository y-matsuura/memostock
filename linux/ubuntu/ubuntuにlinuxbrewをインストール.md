### [参考]
https://qiita.com/thermes/items/926b478ff6e3758ecfea

https://github.com/Linuxbrew/brew

### パッケージインストール
$ sudo apt install build-essential curl git m4 ruby texinfo libbz2-dev libcurl4-openssl-dev libexpat-dev libncurses-dev zlib1g-dev

$ sudo apt install gettext

## 参考
https://docs.brew.sh/Homebrew-on-Linux

### インストールする
#### $ sh -c "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install.sh)"
#### $ test -d ~/.linuxbrew && eval $(~/.linuxbrew/bin/brew shellenv)
#### $ test -d /home/linuxbrew/.linuxbrew && eval $(/home/linuxbrew/.linuxbrew/bin/brew shellenv)
#### $ test -r ~/.bash_profile && echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.bash_profile
#### $ echo "eval \$($(brew --prefix)/bin/brew shellenv)" >>~/.profile

### 確認。エラー出なければOK
$ brew doctor

#### $ sudo mkdir -p /home/linuxbrew/.linuxbrew/var/homebrew/linked
#### $ sudo chown -R $(whoami) /home/linuxbrew/.linuxbrew/var/homebrew/linked

#### $ export PATH="$HOME/.linuxbrew/bin:$PATH"
#### $ export MANPATH="$HOME/.linuxbrew/share/man:$MANPATH"
#### $ export INFOPATH="$HOME/.linuxbrew/share/info:$INFOPATH"
#### $ export LD_LIBRARY_PATH="$HOME/.linuxbrew/lib:$LD_LIBRARY_PATH"

### 確認。エラー出なければOK
$ brew doctor
