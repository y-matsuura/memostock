# 参考
https://qiita.com/funafuna/items/c3bb78a546cf2605205d
# Windows上のフォルダがWSLから見えるか確認
$ `ls -la /mnt/c`
# ホームディレクトリのパスを変更
```
$ sudo vim /etc/passwd
（↓ユーザ名の行を探し/home/xxxを「/mnt/c/linux_home」に変更）
{ubuntu上のユーザ名}:x:1000:1000:,,,:/mnt/c/linux_home:/bin/bash
```
# WSLをexitして再起動
# 反映されているか確認
$ `pwd`
