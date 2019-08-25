# Go環境構築メモ

## 必要なもの
- Mac, Linux
    - git

## やること
- [install goenv](#install-goenv)
- [install go](#install-go)

## install goenv

[goenv](https://github.com/syndbg/goenv)を使ってGoをインストールする.  
`brew`で入れる方法もあるが, より汎用性が高い方法でインストールする. [参考](https://github.com/syndbg/goenv/blob/master/INSTALL.md)  

まずは`goenv`をもってくる.
```
$ git clone https://github.com/syndbg/goenv.git ~/.goenv
```

自分は[zsh](zsh.md)を使っているので, 必要な環境変数を`~/.zshenv`に書き込んでいく.  

```
$ echo 'export GOPATH="$HOME/go"' >> ~/.zshenv
$ echo 'export GOENV_ROOT="$HOME/.goenv"' >> ~/.zshenv
$ echo 'export PATH="$GOENV_ROOT/bin:$PATH"' >> ~/.zshenv
$ echo 'eval "$(goenv init -)"' >> ~/.zshenv
$ echo 'export PATH="$GOPATH/bin:$PATH"' >> ~/.zshenv
```

仮に`~/.zshrc`に`GOPATH`が設定されていると, 読み込む順番の都合でうまく動かなかったりするので消しておく.  

シェルを再起動させる.  

```
$ exec SHELL
$ which goenv

>goenv () {
>	local command
>	command="$1"
>	if [ "$#" -gt 0 ]
>	then
>		shift
>	fi
>	case "$command" in
>		(rehash | shell) eval "$(goenv "sh-$command" "$@")" ;;
>		(*) command goenv "$command" "$@" ;;
>	esac
>}
```

以上でgoenvが動かせるようになる.  

## install go
`goenv`を使って使いたいバージョンのGoを入れていく.  

まずは利用可能なGoのバージョンを確認する.  
```
$ goenv install -l

>Available versions:
>  1.2.2
>  1.3.0
>  ...
>  1.12.8
>  1.12.9
>  1.13beta1
>  1.13rc1
```

とりあえずは安定版の`1.12.9`をインストールする.  

```
$ goenv install 1.12.9
```

現在インストールされているGoのバージョン一覧を確認する.  

```
$ goenv versions

>* system (set by /Users/ryota/.goenv/version) # 元々入れていたGo
>  1.12.9
```

すべてのディレクトリで有効なGoを`1.12.9`にする.  

```
$ goenv global 1.12.9
```

すでに公式インストーラでGoをインストールしている場合, `/usr/local/go/bin`へのパスを消す必要がある.  

```
$ sudo rm -rf /etc/paths.d/go
```

以上でGoが使用可能になるはず.  

```
$ which go

>/Users/ryota/.goenv/shims/go

$ go version

>go version go1.12.9 darwin/amd64
```

ちゃんと指定したバージョンのGoが動いている.  
試しに違うバージョンのGoも入れてみる.

```
$ goenv install 1.11.13
$ goenv global 1.11.13
$ goenv versions

>  system
>* 1.11.13 (set by /Users/ryota/.goenv/version)
>  1.12.9

$ go version

>go version go1.11.13 darwin/amd64
```

できた. Pythonみたいに同じバージョンの環境を複数つくったりできるんだろうか???
