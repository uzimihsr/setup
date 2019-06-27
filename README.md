# Macの設定周りのメモ

## やること一覧

1. システム環境設定
    1. キーボード設定
1. brew
    1. Xcodeのインストール
    1. rubyスクリプトの実行
1. シェルいじり
    1. zsh
    1. prezto
    1. zsh-autosuggestion
    1. zsh-syntax-highlighting
1. iTerm
1. vim

## システム環境設定

### キーボード設定
`りんごマーク -> システム環境設定 -> キーボード`

キーのリピート, リピート入力認識までの時間をどちらも右にフルスイング

<img src="https://github.com/uzimihsr/setup/blob/master/images/keyboard_setting.png" width=50%>

## brew

### Xcodeのインストール
特に詰まるところはないはず. App Storeから落としてくる.

ターミナルを開いて
```
xcode-select --install
```

### rubyスクリプトの実行
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
上記コマンドを打ってもいいし, 心配なら[公式](https://brew.sh/)のコマンドを打つ.
以上問題なければ
```
brew doctor
```
でbrewがちゃんとインストールされているか確認できる.
## シェルいじり
### zsh
シェル一覧を確認
```
cat /etc/shells
>>>
# List of acceptable shells for chpass(1).
# Ftpd will not allow users to connect who are not using
# one of these shells.

/bin/bash
/bin/csh
/bin/ksh
/bin/sh
/bin/tcsh
/bin/zsh
```
こんなんなるはず.  
次にzshをbrew install
```
brew update
brew install zsh
```
もう一度確認
```
cat /etc/shells
>>>
# List of acceptable shells for chpass(1).
# Ftpd will not allow users to connect who are not using
# one of these shells.

/bin/bash
/bin/csh
/bin/ksh
/bin/sh
/bin/tcsh
/bin/zsh
/usr/local/bin/zsh
```
`/usr/local/bin/zsh`が増えていればOK.

### prezto
ログインシェルを変更.
```
chsh -s /usr/local/bin/zsh
echo $SHELL
>>>
/usr/local/bin/zsh
```
ついでに現在のシェルも変更する(またはターミナル再起動).
```
/usr/local/bin/zsh
```
git cloneする. 心配なら[公式](https://github.com/sorin-ionescu/prezto)のコマンドを打つ.
```
git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"
```
zsh設定ファイルへのシンボリックリンクを貼る. 以下をコピペする.
```
setopt EXTENDED_GLOB
for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
  ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
done
```
一応確認. home直下に.zshrc, .zlogin, .zlogout, .zprofile, .zshenvへのシンボリックリンクができているはず.
```
ls -la ~ | grep .zshrc
>>>
.zshrc -> /Users/[ユーザ名]/.zprezto/runcoms/zshrc
```
zshを再起動.
プロンプトを変更. pure一択.
```
vim ~/.zpreztorc
>>>
# Set the prompt theme to load.
# Setting it to 'random' loads a random theme.
# Auto set to 'off' on dumb terminals.
zstyle ':prezto:module:prompt' theme 'sorin' # この行を
zstyle ':prezto:module:prompt' theme 'pure'  # に変更
```
### zsh-autosuggestion

### zsh-syntax-highlighting
