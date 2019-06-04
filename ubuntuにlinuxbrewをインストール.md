[参考]
https://qiita.com/thermes/items/926b478ff6e3758ecfea

### パッケージインストール
$ sudo apt install build-essential curl git m4 ruby texinfo libbz2-dev libcurl4-openssl-dev libexpat-dev libncurses-dev zlib1g-dev

$ sudo apt install gettext

### インストールする
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/linuxbrew/go/install)"

$ export PATH="$HOME/.linuxbrew/bin:$PATH"

$ export MANPATH="$HOME/.linuxbrew/share/man:$MANPATH"

$ export INFOPATH="$HOME/.linuxbrew/share/info:$INFOPATH"

$ export LD_LIBRARY_PATH="$HOME/.linuxbrew/lib:$LD_LIBRARY_PATH"

### 確認。エラー出なければOK
$ brew doctor
