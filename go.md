# Go環境構築メモ

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
$ exec $SHELL -l
```

自分は[zsh](zsh.md)を使っているので, goを使うために必要な環境変数を`~/.zshrc`に書き込んでいく.  

```
$ echo 'export PATH="$GOPATH/bin:$PATH"' >> ~/.zshrc
$ echo 'export PATH="$GOPATH/bin:$PATH"' >> ~/.zshrc
```

以上でgoenvが動かせるようになる.  

## install go
goenvを使って使いたいバージョンのGoを入れていく.  

まずは利用可能なGoのバージョンを確認する.  
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
