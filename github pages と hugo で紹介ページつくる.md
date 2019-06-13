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

#### install theme
https://themes.gohugo.io/academic/#install

$ git clone https://github.com/sourcethemes/academic-kickstart.git MyAcademic

$ cd ~/matsuura/workspace/selfintroduction/theme/MyAcademic

$ git submodule update --init --recursive

#### confirm
$ cd ~/matsuura/workspace/selfintroduction/theme/MyAcademic

$ hugo server

`http://localhost:1313` にアクセス

### githubで公開してみる
#### githubでリポジトリをつくる
#### edit config
```
baseurl = "https://y-matsuura.github.io/introduction"
theme = "MyAcademic"
canonifyurls = true
```

#### exec build
$ cd ~/matsuura/workspace/selfintroduction/theme/MyAcademic

$ hugo

#### move public
$ cd ~/matsuura/workspace/selfintroduction/theme/MyAcademic/public

#### push git
```
$ git init
$ git remote add origin git@github.com:y-matsuura/introduction.git
$ git add -A
$ git commit -m 'initial commit'
$ git push origin master
```

#### change github-pages
```
・githubでintroductionリポジトリのsettingをひらく
・GitHub Pagesのsourceを master branch に変更する 
```

#### confirm
`Your site is ready to be published at https://y-matsuura.github.io/introduction/. ` をクリック
