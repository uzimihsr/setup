# anyenv導入メモ
Goとかのプログラミング言語の環境管理ツール(〜env系)を管理する便利な[anyenv](https://github.com/anyenv/anyenv)をインストールする.

## 必要なもの
- Mac
    - git

## やること
- [install anyenv](#install-anyenv)

## install anyenv
[README](https://github.com/anyenv/anyenv#manual-git-checkout)の通りに進める.  

まずはanyenvをgit cloneし, PATHに`$HOME/.anyenv/bin`を通す.  
```
$ git clone https://github.com/anyenv/anyenv ~/.anyenv
$ echo 'export PATH="$HOME/.anyenv/bin:$PATH"' >> ~/.zshrc
```

anyenvをzsh用にセットアップする.  
`eval "$(anyenv init -)"`を`~/.zshrc`に追加しろと言われるので従う.
```
$ ~/.anyenv/bin/anyenv init
# Load anyenv automatically by adding
# the following to ~/.zshrc:

eval "$(anyenv init -)"

$ echo 'eval "$(anyenv init -)"' >> ~/.zshrc
```

シェルを再起動.  
マニフェストディレクトリが無いよ的なことを言われるのでそのまま従う.  
```
$ exec $SHELL -l
ANYENV_DEFINITION_ROOT(/Users/username/.config/anyenv/anyenv-install) doesn't exist. You can initialize it by:
> anyenv install --init

$ anyenv install --init
Manifest directory doesn't exist: /Users/username/.config/anyenv/anyenv-install
Do you want to checkout ? [y/N]: y
Cloning https://github.com/anyenv/anyenv-install.git master to /Users/username/.config/anyenv/anyenv-install...
Cloning into '/Users/username/.config/anyenv/anyenv-install'...
remote: Enumerating objects: 48, done.
remote: Total 48 (delta 0), reused 0 (delta 0), pack-reused 48
Unpacking objects: 100% (48/48), done.

Completed!
```

これでanyenvを使う準備が完了.  
出てきた~envの中から必要に応じてインストールする.  
```
$ anyenv
anyenv 1.1.1
Usage: anyenv <command> [<args>]

Some useful anyenv commands are:
   commands            List all available anyenv commands
   local               Show the local application-specific Any version
   global              Show the global Any version
   install             Install a **env
   uninstall           Uninstall a specific **env
   version             Show the current Any version and its origin
   versions            List all Any versions available to **env

See `anyenv help <command>' for information on a specific command.
For full documentation, see: https://github.com/anyenv/anyenv#readme

$ anyenv install -l
Renv
crenv
denv
erlenv
exenv
goenv
hsenv
jenv
luaenv
nodenv
phpenv
plenv
pyenv
rbenv
sbtenv
scalaenv
swiftenv
tfenv
```
