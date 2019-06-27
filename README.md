# Macの設定周りのメモ

## やること一覧

1. システム環境設定
    1. キーボード設定
1. brew
    1. Xcodeのインストール
    1. rubyスクリプトの実行
1. zsh
    1. zsh
    1. prezto
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

## zsh
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

## prezto
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
