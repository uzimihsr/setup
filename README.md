# Macの設定周りのメモ

## やること一覧

1. システム環境設定
    1. キーボード設定
1. brew
    1. Xcodeのインストール
    1. rubyスクリプトの実行
1. zsh
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
```bash
xcode-select --install
```

### rubyスクリプトの実行
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
上記コマンドを打ってもいいし, 心配なら[公式](https://brew.sh/)のコマンドを打つ.
以上問題なければ
```bash
brew doctor
```
でbrewがちゃんとインストールされているか確認できる.
