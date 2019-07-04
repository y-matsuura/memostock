# 前提
```
現場で支給されたPCがWindows10Proだったので、
当初はDocker for Windows を使おうとしていたが、
案件で ubuntu のデスクトップが必要となり、当時はdockerでubunutuデスクトップをつくる方法がわからず、
仕方なく vagrant + virtualbox で ubuntuデスクトップを立ち上げていた。
それもあって、開発の際には vagrant + virtualbox に各環境を構築していた。
環境が重いと感じてきたので、Docker for Windows に再挑戦！
```
# Hyper-v を有効にする
https://docs.microsoft.com/ja-jp/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v

# Docker for windows ダウンロード
https://docs.docker.com/docker-for-windows/install/

# Docker for Windows インストール
ダウンロードした `Docker for Windows Installer.exe` を実行

# 確認
`docker --version`
