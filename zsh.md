# zsh設定メモ

## 必要なもの
- Mac
    - brew
- Debian
    - apt-get
- Red Hat
    - yum
- Windows
    - 知らん
- 共通
    - git

## やること
- [install zsh](#install-zsh)
- [install prezto](#install-prezto)
- [enable zsh-syntax-highlighting](#enable-zsh-syntax-highlighting)
- [enable zsh-autosuggestions](#enable-zsh-autosuggestions)
- [enable zsh-completions](#enable-zsh-completions)

## install zsh

**Macの場合**  
brewで入れる.  
```bash
$ brew update
$ brew install zsh
```

`/usr/local/bin/zsh`にインストールされるはず.  

**ログインシェルの変更**  
ログインしたときに立ち上がるシェルをzshに変更する.  
```bash
# 使えるシェルの一覧を確認
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
/usr/local/bin/zsh # こいつを使いたい

# ログインシェルを変更
$ chsh -s /usr/local/bin/zsh
```

## install prezto

**preztoのインストール**  

[prezto](https://github.com/sorin-ionescu/prezto)をgit cloneして,  
home直下にzsh設定ファイル(`.zshrc`, `.zlogin`, `.zlogout`, `.zprofile`, `.zshenv`)へのシンボリックリンクを張る.  

```bash
# git clone
$ git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"

# シンボリックリンクを張る
$ setopt EXTENDED_GLOB
for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
  ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
done
```

**プロンプトの変更**  

`.zpreztorc`を編集してプロンプトを変更する. pureが好き.  

```bash
$ vim ~/.zpreztorc
...
# Set the prompt theme to load.
# Setting it to 'random' loads a random theme.
# Auto set to 'off' on dumb terminals.
zstyle ':prezto:module:prompt' theme 'sorin' # この行を
zstyle ':prezto:module:prompt' theme 'pure'  # に変更
...
```

## enable zsh-syntax-highlighting

`.zpreztorc`に記述する.  

```bash
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
  'syntax-highlighting' \ # この行を追加
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

## enable zsh-autosuggestions

`.zpreztorc`に記述する.  

```bash
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
  'autosuggestions'\ # この行を追加
  'prompt'
...
```

補完関数は`~/.zprezto/modules/completion/external/src`に配置されている.  
自作したやつとかを追加したかったらここに書いていいと思う.  

## enable zsh-completions

デフォルトで有効になっているはず.  

```bash
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
  'completion' \ # この行があればOK
  'syntax-highlighting'\
  'autosuggestions'\
  'prompt'
...
```

## setup for Kubernetes
kubectlの補完  
```bash
echo 'source <(kubectl completion zsh)' >> ~/.zshrc
```

プロンプトにkubeの情報を表示させる  
```bash
# Macの場合
$ brew install kube-ps1

# それ以外の場合
$ git clone https://github.com/jonmosco/kube-ps1.git
$ cp kube-ps1/kube-ps1.sh /usr/local/opt/kube-ps1/share/kube-ps1.sh
```

`~/.zshrc`に以下の記述を追加  
```bash
source "/usr/local/opt/kube-ps1/share/kube-ps1.sh"
PS1='$(kube_ps1)'$PS1
kubeoff
```
`$ kubeon`, `$ kubeoff`で表示/非表示の切り替えができる.  


## future
なんかいいのあったら足していこう  
