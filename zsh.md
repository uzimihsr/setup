# zsh設定メモ

## 前提条件
- mac
    - brew
- git

## やること
- [install zsh](#install-zsh)
- [install prezto](#install-prezto)
- [install zsh-syntax-highlighting](#install-zsh-syntax-highlighting)
- [install zsh-autosuggestions](#install-zsh-autosuggestions)

## install zsh

macの場合:

```
$ brew update
$ brew install zsh
```

`/usr/local/bin/zsh`にインストールされるはず.  

使えるシェルの一覧を確認.

```
$ cat /etc/shells

# List of acceptable shells for chpass(1).
# Ftpd will not allow users to connect who are not using
# one of these shells.
/bin/bash
/bin/csh
/bin/ksh
/bin/sh
/bin/tcsh
/bin/zsh
/usr/local/bin/zsh # この行が追加されてない場合は追記する
```

ログインシェルを変更する

```
$ chsh -s /usr/local/bin/zsh
```

terminalを再起動.

## install prezto

preztoをgit clone

```
$ git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"
```

または[公式](https://github.com/sorin-ionescu/prezto)のコマンドを打つ.

zsh設定ファイルへのシンボリックリンクを貼る. 以下をコピペする.

```
$ setopt EXTENDED_GLOB
for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
  ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
done
```

home直下に.zshrc, .zlogin, .zlogout, .zprofile, .zshenvへのシンボリックリンクができているはず.

`.zpreztorc`を編集, プロンプトを変更. pure一択.

```
$ vim ~/.zpreztorc

...
# Set the prompt theme to load.
# Setting it to 'random' loads a random theme.
# Auto set to 'off' on dumb terminals.
zstyle ':prezto:module:prompt' theme 'sorin' # この行を
zstyle ':prezto:module:prompt' theme 'pure'  # に変更
...
```

terminalを再起動.

## install zsh-syntax-highlighting

`.zpreztorc`に記述
```
$ vim ~/.zpreztorc

...
#
# General
#
...
# Set the Prezto modules to load (browse modules).
# The order matters.
zstyle ':prezto:load' pmodule \
  'environment' \
  'terminal' \
  'editor' \
  'history' \
  'directory' \
  'spectrum' \
  'utility' \
  'completion' \
  'syntax-highlighting'\ # この行を追加
  'prompt'
...
#
# Syntax Highlighting
#
#----ここから----#
# syntax-highlighting
zstyle ':prezto:module:syntax-highlighting' color 'yes'

# Set syntax highlighters.
# By default, only the main highlighter is enabled.
 zstyle ':prezto:module:syntax-highlighting' highlighters \
   'main' \
   'brackets' \
   'pattern' \
   'line' \
   'cursor' \
   'root'
#----ここまで追加----#
# 多分デフォルトコメントアウトされているのではずすだけでもOK
...
```

## install zsh-autosuggestions

`.zpreztorc`に記述
```
$ vim ~/.zpreztorc

...
#
# General
#
...
# Set the Prezto modules to load (browse modules).
# The order matters.
zstyle ':prezto:load' pmodule \
  'environment' \
  'terminal' \
  'editor' \
  'history' \
  'directory' \
  'spectrum' \
  'utility' \
  'completion' \
  'syntax-highlighting'\
  'autosuggestions'\ // この行を追加
  'prompt'
...
```

terminalを再起動.
