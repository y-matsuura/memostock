#### まとめ
https://togetter.com/li/1392604

https://qiita.com/kanimisonson/items/922e43dafc2bc484bf69

#### 設定の一覧表示
git config -l

#### 名前とメアドを設定する
git config --global user.name apc-matsuura

git config --global user.email yuji.matsura@ap-com.co.jp

#### 改行など
git config --global core.autocrlf input

git config --global core.safecrlf warn

#### ローカルリポジトリを最新にする
git pull --rebase origin develop

git fetch // 先にリモートの状態をリモート追跡ブランチにコピー

git merge origin/master // リモートのコピーからマージ

#### ブランチをつくる
git checkout -b ブランチ名

git checkout -b master/matsuura

#### 変更を一時退避する
git stash save

#### 退避した作業を戻す
git stash apply stash@{0}

#### 退避した作業を消す
git stash drop stash@{0}

#### リモートにpushする
git push origin develop_/matsuura

#### カレントブランチをpushする
git push origin HEAD

git push -u origin develop_/matsuura

#### コミット取り消し
##### 直前のコミット取り消し
git reset --soft HEAD^

##### 最初のコミットを取り消し
git update-ref -d HEAD

#### ブランチ(branch)を切り替えてソースを取得
git checkout -b ブランチ名 リモートブランチ名

#### push取り消し
https://reasonable-code.com/git-push-cancel/

##### 強制取り消し
```
１．リモートの master 参照を強制に戻す
git push -f origin 8dj2dg:master
```

##### revert使う
```
１．取り消したいコミットのコミットIDを取得する。
git log

２．取り消したいコミットをrevertする。
git revert <commit id>

※Merge commit の場合
git revert -m 1 <commit id>

３．リモートへpushする
git push origin ブランチ名
```

#### gitで違うユーザでコミット&プッシュしてしまった時の対処法
https://hacknote.jp/archives/28489/
```
１．間違えたプッシュをリモートから取り消し
git push -f origin HEAD^:[ブランチ名]

２．間違えたコミットを取り消し
git reset --soft HEAD^

３．ユーザー名変更
[例]
git config --global user.name apc-matsuura
git config --global user.email yuji.matsura@ap-com.co.jp
```

#### developへのマージ作業
```
■ローカルで作業完了したブランチをコミット・プッシュ
git commit
git push origin ローカルブランチ
[例]
git push origin develop_/matsuura

■マージ先のブランチに移動
git checkout develop

■マージ先のブランチを最新にする
git fetch origin
git merge origin/develop

■マージする
git merge --no-ff マージしたいブランチ（ローカルブランチ）
[例]
git merge --no-ff develop_/matsuura

■プッシュする
git push

※confilictした場合
[参考]
https://qiita.com/kyoyyy/items/92c46ea10654ea638398
```

#### リモートブランチ削除
```
git push --delete origin branchname
[例]
git push --delete origin develop_/matsuura

git checkout -b develop_/matsuura
```

# ファイルのリネーム
```
git mv 変更前 変更後
[例]
git mv search.html Search.html
```

#### 接続を確かめる
```
ssh git@github.com

ssh -T git@github.com

ssh -vT git@github.com

ssh -T Host
```

#### Githubに登録しているssh公開鍵を取得する方法
```
https://github.com/{userName}.keys

[参考]
https://qiita.com/shuntaro_tamura/items/0b2c3ef36c5bbe25e622

clip < ~/.ssh/id_rsa_aws-sdk.pub

git@github.com:tamac-io/aws-sdk-for-ruby.git

git remote set-url origin git@github.com:[ユーザID]/[リポジトリ].git

git remote set-url origin [Host名]:[ユーザID]/[リポジトリ].git

ssh -T dns2-web
ssh -T aws-sdk

git remote set-url origin aws-sdk-for-ruby:git/aws-sdk-for-ruby.git
```

#### リモートブランチを削除する
```
$ git branch --remote
$ git push --delete origin 【ブランチ名】

git push --delete origin develop_/matsuura-agent-verify
```

#### Githubで特定のpull requestをローカルに持ってくる
```
[例：BRANCHNAME]
sre-jenkinsで実行するためのJenkinsfileを追加

■fetch
git fetch origin/ID/head:BRANCHNAME

（例）
git fetch origin/109/head:sre-jenkinsで実行するためのJenkinsfileを追加

■checkout
git checkout BRANCHNAME

（例）
git checkout sre-jenkinsで実行するためのJenkinsfileを追加

[参考]
https://qiita.com/tarr1124/items/d807887418671adbc46f
https://help.github.com/articles/checking-out-pull-requests-locally/
```

#### git CUI 上でツリー表示する
```
[設定]
git config --add alias.tree "log --graph --pretty='format:%C(yellow)%h%Creset %s %Cgreen(%an)%Creset %Cred%d%Creset'"

[コマンド]
git tree --all


#### git clone
##### 特定のブランチを指定する
git clone -b develop_/matsuura-eol https://github.com/tamac-io/dns2-app.git dns2-app-eol

#### diffを取得
```
git diff origin/develop origin/develop_/matsuura-eol

git archive origin/develop_/matsuura-eol `git diff --name-only origin/develop origin/develop_/matsuura-eol --diff-filter=ACMR` -o archive.zip

git archive archive origin/develop_/matsuura-eol --format=zip -o 出力ファイル名 --prefix=data/ `git diff --name-only --diff-filter=d コミット1 コミット2`
```

#### コミットログを整理
```
コミットログを確認
git log --graph --oneline

(例)
git config --global alias.tree "log --graph --pretty='format:%C(yellow)%h%Creset %s %Cgreen(%an)%Creset %Cred%d%Creset'"
```

#### リベース指示書を作成
```
git rebase -i コミットid

git rebase -i リモートブランチ
（例）
git rebase -i origin/develop

※注意
指定するコミットidは、リベースしたいところの一つ前。
例えば「commit_id_2」「commit_id_3」をリベースしたい場合、
指定するのは「commit_id_1」になる。
（例）
commit_id_3 commitメッセージ(2017/03/01)
commit_id_2 commitメッセージ(2017/02/01)
commit_id_1 commitメッセージ(2017/01/01)

(p)pick：コミットをそのまま残す。
(r)reword：コミットメッセージを変更。
(e)edit	：コミット自体の内容を編集。
(s)squash：直前のpickを指定したコミットに統合。メッセージも統合。
(f)fixup：直前のpickを指定したコミットに統合。メッセージは破棄。

git push ブランチ -f
```

#### プルリクまでつくったブランチの名前を変える
```
※pushしたリモートブランチの名前を直接変更することはできないらしい

１．ローカルで対象のブランチの名前を変更する
１－１．ブランチを指定して変更する
git branch -m 変更したいブランチ名 変更後の名前
（例）
git branch -m develop_/matsuura-eol IRUCA-1801

１－２．現在のブランチを変更する
git branch -m 変更後の名前
（例）
git branch -m IRUCA-1801

２．変更したローカルブランチをpushする
git push origin IRUCA-1801

３．新たにpushしたブランチのプルリクつくる

４．古いプルリクをcloseする

５．リモートの古いブランチを削除する
５－１．
git push --delete origin 変更したいブランチ名
５－２．
git push origin :変更したいブランチ名
（例）
git push --delete origin develop_/matsuura-eol
git push origin :develop_/matsuura-eol

６．古い名前のリモート追跡ブランチも削除
６－１．
git branch -dr old-branch
６－２．
git branch --delete --remotes old-branch
```


#### ローカルブランチの確認
git branch

#### ローカルブランチを削除
git branch -D [ブランチ名]
