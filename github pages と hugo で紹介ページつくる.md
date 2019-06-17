#### install linuxbrew
https://github.com/y-matsuura/memostock/blob/master/linux/ubuntu/ubuntu%E3%81%ABlinuxbrew%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB.md

#### install hugo
$ brew install hugo

#### create workspace
https://qiita.com/ryoma-tokushige/items/eba3e6cd415e9755af87

##### 例
$ mkdir ~/matsuura/workspace

#### create introduction 
$ hugo new site selfintroduction

#### confirm
$ cd ~/matsuura/workspace/selfintroduction

$ hugo server

`http://localhost:1313` にアクセス
※この時点では画面はまっしろ

#### install theme
http://www.mit.edu/~k2smith/post/getting-started/

$ cd ~/matsuura/workspace/selfintroduction

$ git init

$ git submodule add https://github.com/gcushen/hugo-academic.git themes/academic

#### confirm

$ cd ~/matsuura/workspace/selfintroduction

$ cp -av themes/academic/exampleSite/* .

$ hugo server

`http://localhost:1313` にアクセス

### githubで公開してみる
#### githubでリポジトリをつくる
#### edit config
```
baseurl = "https://y-matsuura.github.io/selfintroduction/"
theme = "academic"
canonifyurls = true
publishDir = "docs"
```

#### exec build
$ cd ~/matsuura/workspace/selfintroduction

$ hugo

#### push git
```
$ git remote add origin git@github.com:y-matsuura/selfintroduction.git
$ git add -A
$ git commit -m 'initial commit'
$ git push origin master
```

#### change github-pages
```
・githubでintroductionリポジトリのsettingをひらく
・GitHub Pagesのsourceを master/docs に変更する 
```

#### confirm
`Your site is ready to be published at https://y-matsuura.github.io/selfintroduction/. ` をクリック

#### cusomise
##### アイコン
https://fontawesome.com/icons?d=gallery&s=brands
