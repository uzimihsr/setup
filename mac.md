# Macの設定周りのメモ

## やること
- [keyboard setting](#keyboard-setting)
- [install brew](#install-brew)

## keyboard setting

`システム環境設定 -> キーボード`

キーのリピート, リピート入力認識までの時間をどちらも右にフルスイング

![キーボード設定画面](images/keyboard_setting.png)

## install brew

[Xcode](https://apps.apple.com/jp/app/xcode/id497799835?mt=12)を落としてくる.
ターミナルを開いて
```
$ xcode-select --install
```

rubyスクリプトを動かす.
```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
上記コマンドを打ってもいいし, 心配なら[公式](https://brew.sh/)のコマンドを打つ.
以上問題なければ
```
$ brew doctor
```
でbrewがちゃんとインストールされているか確認できる.

## install cheatsheet

[CheatSheet](https://www.cheatsheetapp.com/CheatSheet/)をダウンロード.
