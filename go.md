# Go環境構築メモ
Goのセットアップ

## 必要なもの
- Mac
    - git
    - [anyenv](anyenv.md)

## やること
- [install goenv](#install-goenv)
- [install go](#install-go)

## install goenv
anyenvを使って[goenv](https://github.com/syndbg/goenv)をインストールし, そのgoenvを使ってGoをインストールする.  

まずはgoenvをもってくる.
```
$ anyenv install goenv
/var/folders/t7/qck11mhn5fj4q6r1mbdf2nxw0000gn/T/goenv.20190905230244.938 ~
Cloning https://github.com/syndbg/goenv.git master to goenv...
Cloning into 'goenv'...
remote: Enumerating objects: 72, done.
remote: Counting objects: 100% (72/72), done.
remote: Compressing objects: 100% (48/48), done.
remote: Total 13907 (delta 32), reused 43 (delta 18), pack-reused 13835
Receiving objects: 100% (13907/13907), 2.51 MiB | 2.55 MiB/s, done.
Resolving deltas: 100% (9510/9510), done.
~

Install goenv succeeded!
Please reload your profile (exec $SHELL -l) or open a new session.

$ exec $SHELL -l
$ goenv
goenv 2.0.0beta11
Usage: goenv <command> [<args>]

Some useful goenv commands are:
   commands    List all available commands of goenv
   local       Set or show the local application-specific Go version
   global      Set or show the global Go version
   shell       Set or show the shell-specific Go version
   install     Install a Go version using go-build
   uninstall   Uninstall a specific Go version
   rehash      Rehash goenv shims (run this after installing executables)
   version     Show the current Go version and its origin
   versions    List all Go versions available to goenv
   which       Display the full path to an executable
   whence      List all Go versions that contain the given executable

See 'goenv help <command>' for information on a specific command.
For full documentation, see: https://github.com/syndbg/goenv#readme
```
以上でgoenvが動かせるようになる.  

## install go
goenvを使って使いたいバージョンのGoを入れていく.  

その前にgoを使うために必要な環境変数を`~/.zshrc`に書き込む.  

```
$ echo 'export PATH="$GOPATH/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="$GOPATH/bin:$PATH"' >> ~/.zshrc
```

利用可能なGoのバージョンを確認する.  
```
$ goenv install -l
Available versions:
  1.2.2
  1.3.0
  ...
  1.12.9
  1.13.0
  1.13beta1
  1.13rc1
  1.13rc2
```

とりあえずは安定版の`1.13.0`をインストールする.  
```
$ goenv install 1.13.0
Downloading go1.13.darwin-amd64.tar.gz...
-> https://dl.google.com/go/go1.13.darwin-amd64.tar.gz
Installing Go Darwin 64bit 1.13.0...
Installed Go Darwin 64bit 1.13.0 to /Users/username/.anyenv/envs/goenv/versions/1.13.0
```

現在インストールされているGoのバージョン一覧を確認する.  
```
$ goenv versions
  1.13.0
```

すべてのディレクトリで有効なGoを`1.13.0`にする.  
`goenv rehash`の後にシェルを再起動しないとPATHが通らないので注意.
```
$ goenv global 1.13.0
$ goenv rehash
$ exec $SHELL -l
```

以上でGoが使用可能になるはずなので, 動作確認してみる.  
goenvを使っている場合`GOPATH`はGoのバージョンごとに勝手に管理してくれる. 便利.  
```
$ which go
/Users/username/.anyenv/envs/goenv/shims/go

$ go version
go version go1.13 darwin/amd64

$ echo $GOPATH
/Users/username/go/1.13.0
```

試しに違うバージョンのGoも入れてみる.
```
$ goenv install 1.12.9
Downloading go1.12.9.darwin-amd64.tar.gz...
-> https://dl.google.com/go/go1.12.9.darwin-amd64.tar.gz
Installing Go Darwin 64bit 1.12.9...
Installed Go Darwin 64bit 1.12.9 to /Users/ryota/.anyenv/envs/goenv/versions/1.12.9

$ goenv global 1.12.9
$ goenv rehash
$ exec $SHELL -l
$ goenv versions
* 1.12.9 (set by /Users/username/.anyenv/envs/goenv/version)
  1.13.0

$ go version
go version go1.12.9 darwin/amd64

$ echo $GOPATH
/Users/ryota/go/1.12.9
```

以上. 必要に応じてGoのバージョンを変えていきたい.
