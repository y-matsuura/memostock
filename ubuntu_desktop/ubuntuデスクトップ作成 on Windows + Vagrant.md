
https://qiita.com/mhagita/items/8f339106c3b48eb098ca

https://thejuraku.com/pc/ubuntu%E3%81%A7%E3%82%AD%E3%83%BC%E3%83%9C%E3%83%BC%E3%83%89%E3%83%AC%E3%82%A4%E3%82%A2%E3%82%A6%E3%83%88%E5%A4%89%E6%9B%B4/

▼VMにubuntu構築
------------------------------------------------------------------------------------------
Vagrantfile作成
$ vi Vagrantfile
$ vagrant up
起動後
$ sudo apt update
キーボードのレイアウト選択

// ubuntu-desktopをインストール
$ sudo apt install ubuntu-desktop

// 再起動
$ sudo reboot
------------------------------------------------------------------------------------------


▼日本語入力できるようにする
------------------------------------------------------------------------------------------
// ubuntuを更新
https://qiita.com/masoo/items/8ebc51a6a9f32417d4a3
$ sudo apt update
$ sudo apt dist-upgrade
$ sudo apt autoremove

// 日本語環境つくる
https://kledgeb.blogspot.com/2018/04/ubuntu-1804-91.html

// Mozcインストール
https://www.karelie.net/install-ibus-mozc-1804/

// 辞書をダウンロード
// ダウンロードしたディレクトリに移動
$ cd ~/Downloads

// 辞書を解凍
$ tar xavf {辞書ファイル}

// 解凍したディレクトリに移動
$ cd {辞書ディレクトリ}

// あるファイル内のコードを修正
$ sed -i s/'const bool kActivatedOnLaunch = false;'/'const bool kActivatedOnLaunch = true;'/g mut/src/unix/ibus/property_handler.cc

// 辞書ビルドに必要なパッケージをインストール
$ sudo apt update && sudo apt upgrade -y && sudo apt install -y devscripts autoconf automake autopoint autotools-dev build-essential debhelper dh-autoreconf dh-strip-nondeterminism dpkg-dev fcitx-bin fcitx-libs-dev g++ g++-7 gcc gcc-7 gir1.2-fcitx-1.0 gir1.2-gtk-2.0 gir1.2-harfbuzz-0.0 gyp icu-devtools libasan4 libatk1.0-dev libatomic1 libc-dev-bin libc6-dev libcairo-script-interpreter2 libcairo2-dev libcilkrts5 libdbus-1-dev libdrm-dev libegl1-mesa-dev libexpat1-dev libfcitx-config4 libfcitx-core0 libfcitx-gclient1 libfcitx-qt0 libfcitx-utils0 libfile-stripnondeterminism-perl libfontconfig1-dev libfreetype6-dev libgcc-7-dev libgcroots-dev libgcroots0 libgdk-pixbuf2.0-dev libgettextpo0 libgl1-mesa-dev libgles2-mesa-dev libglib2.0-dev libglib2.0-dev-bin libglu1-mesa-dev libglvnd-core-dev libglvnd-dev libgraphite2-dev libgtk2.0-dev libgwengui-cpp0 libgwengui-qt5-0 libgwengui-qt5-dev libgwenhywfar-core-dev libgwenhywfar-data libgwenhywfar60 libharfbuzz-dev libharfbuzz-gobject0 libibus-1.0-dev libice-dev libicu-dev libicu-le-hb-dev libicu-le-hb0 libiculx60 libitm1 liblsan0 libmng2 libmpx2 libopengl0 libpango1.0-dev libpcre16-3 libpcre3-dev libpcre32-3 libpcrecpp0v5 libpixman-1-dev libpng-dev libprotobuf-dev libprotobuf-lite10 libprotoc10 libpthread-stubs0-dev libpython-dev libpython-stdlib libpython2.7-dev libqt4-dbus libqt4-declarative libqt4-network libqt4-script libqt4-sql libqt4-xml libqt4-xmlpatterns libqt5concurrent5 libqt5designer5 libqt5opengl5 libqt5printsupport5 libqt5sql5 libqt5test5 libqt5xml5 libqtcore4 libqtdbus4 libqtgui4 libquadmath0 libqwt-headers libqwt-qt5-6 libqwt-qt5-dev libsigsegv2 libsm-dev libstdc++-7-dev libtool libtsan0 libubsan0 libuim-custom2 libuim-dev libuim-scm0 libuim8 libwayland-bin libwayland-dev libx11-dev libx11-xcb-dev libxau-dev libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev libxcb-present-dev libxcb-randr0-dev libxcb-render0-dev libxcb-shape0-dev libxcb-shm0-dev libxcb-sync-dev libxcb-xfixes0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-utils libxrandr-dev libxrender-dev libxshmfence-dev libxxf86vm-dev libzinnia-dev linux-libc-dev m4 make mesa-common-dev ninja-build pkg-config po-debconf protobuf-compiler python python-dev python-minimal python-pkg-resources python2.7 python2.7-dev python2.7-minimal python3-distutils python3-lib2to3 qdbus qt5-qmake qt5-qmake-bin qtbase5-dev qtbase5-dev-tools qtchooser qtcore4-l10n x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-randr-dev x11proto-xext-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xorg-sgml-doctools xtrans-dev zlib1g-dev

// ビルド
$ sudo ./build_mozc_plus_utdict

// ビルドしたMozc UT2 をインストール
$ sudo dpkg -i ./mozc-data_*.deb ./mozc-server_*.deb ./mozc-utils-gui_*.deb ./ibus-mozc_*.deb

// 再起動
$ sudo reboot

// 日本語キーボードになっていない場合
$ setxkbmap -print -verbose 10
$ setxkbmap -layout jp

▼たぶんこっちの方がよい
$ sudo dpkg-reconfigure keyboard-configuration
[参考]
https://qiita.com/jimaz/items/af134896483ae9d32a7d

// ubuntuを更新
$ sudo apt update
$ sudo apt dist-upgrade
$ sudo apt autoremove

------------------------------------------------------------------------------------------


▼gitを利用できるようにする
------------------------------------------------------------------------------------------
// gitがインストールされているか確認
$ git --version

// バージョンが古い場合は削除
$ sudo apt remove git
[参考]
https://gist.github.com/pokisin/fc4bf37a5ced0e6f7fe6e45333e37b4f

// 必要なパッケージをインストール
※随時追加する
$ sudo apt install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev
$ sudo apt install asciidoc xmlto docbook2x
$ sudo apt install autoconf

// wgetインストール
$ sudo apt install wget
$ wget -qO- https://wtfismyip.com/text

// gitインストール
https://www.task-notes.com/entry/20170507/1494126000
$ wget https://github.com/git/git/archive/v2.21.0.tar.gz

// 展開する
$ tar -kxf v2.21.0.tar.gz
    ※オプション -f：アーカイブファイル名を指定する
    ※オプション -x：アーカイブされたファイルを解凍し展開・復元を行う
    ※オプション -k：解凍した際に既存のファイルを置き換えない

// 移動する
$ cd git-2.21.0

// コンパイルしてインストール
[Git公式]
$ make configure
$ ./configure
$ make all doc info
$ sudo make install install-doc install-html install-info

or

[下記でもOK]
$ make all && sudo make prefix=/usr/local install

// gitのバージョン確認する
$ git --version
------------------------------------------------------------------------------------------


▼エディタをインストールする
------------------------------------------------------------------------------------------
// vimインストール
$ sudo apt install vim
$ dpkg -l vim

// atomインストール
$ sudo add-apt-repository ppa:webupd8team/atom
$ sudo apt update
$ sudo apt install atom
------------------------------------------------------------------------------------------



